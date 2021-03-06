
==================
    Contribute
==================


Introduction
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Feel free and welcome to contribute to this project. You can start
with filing issues and ideas for improvement in GitHub tracker__.
My favorite thoughts from The Zen of Python:

* Beautiful is better than ugly.
* Simple is better than complex.
* Readability counts.

A couple of recommendations from `PEP8`__ and myself:

* Comments should be complete sentences.
* The first word should be capitalized (unless identifier).
* When using hanging indent, the first line should be empty.

__ https://github.com/psss/did/issues
__ https://www.python.org/dev/peps/pep-0008/


Start
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Clone the git repository, create a virtual environment and use
``pip`` to install ``did`` with all necessary dependencies. This
will also link python modules from the repo so that you can test
directly the modified code::

    git clone https://github.com/psss/did
    cd did
    mkvirtualenv did
    pip install --editable .[all]

Install `virtualenvwrapper`__ if you do not have it already on
your system. It makes working with virtual environments much
easier.

__ https://virtualenvwrapper.readthedocs.io/


Makefile
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

There are several Makefile targets defined to make the common
daily tasks easy & efficient:

make test
    Execute the test suite.

make smoke
    Perform quick basic functionality test.

make coverage
    Run the test suite under coverage and report results.

make docs
    Build documentation.

make packages
    Build rpm and srpm packages.

make hooks
    Link git commit hooks.

make tags
    Create or update the Vim ``tags`` file for quick searching.
    You might want to use ``set tags=./tags;`` in your ``.vimrc``
    to enable parent directory search for the tags file as well.

make clean
    Cleanup all temporary files.


Commits
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It is challenging to be both concise and descriptive, but that is
what a well-written summary should do. Consider the commit message
as something that could/will be pasted into release notes:

* The first line should have up to 50 characters.
* Complete sentence with the first word capitalized.
* Should concisely describe the purpose of the patch.
* Other details should be separated by a blank line.

Why should I care?

* It helps others (and yourself) find relevant commits quickly.
* The summary line can be re-used later (e.g. for rpm changelog).
* Some tools do not handle wrapping, so it is then hard to read.
* You will make the maintainer happy to read beautiful commits :)

You can get some more context in the `stackoverflow`__ article.

__ http://stackoverflow.com/questions/2290016/


Hooks
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can find git commit hooks in the ``examples`` directory.
Consider linking or copying them into your git config::

    GIT=~/git/did # Update to your actual path
    ln -snf $GIT/hooks/pre-commit $GIT/.git/hooks
    ln -snf $GIT/hooks/commit-msg $GIT/.git/hooks

Or simply run ``make hooks`` which will do the linking for you.
Note that this will overwrite existing hooks.


Tests
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

To run tests using pytest::

    coverage run --source=did -m py.test tests
    coverage report

Install pytest and coverage using yum::

    yum install pytest python-coverage

or pip::

    pip install .[tests]

See Travis CI and Coveralls for the latest test/coverage results:

* https://travis-ci.org/psss/did/builds
* https://coveralls.io/github/psss/did


Docs
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For building documentation locally install necessary modules::

    pip install .[docs]

Building documentation is then quite straightforward::

    make docs

Find the resulting html pages under the ``docs/_build/html``
folder.


MrBob
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can use also use `mrbob` to easily create templates to help
you get started contributing::

    pip install mr.bob
    mrbob examples/mr.bob/plugin -O ./did/plugins

`mrbob` should have asked you a few questions before creating a
new basic Stats plugin for you in `did/plugins/`. Check `git
status` to see the new files it created as a result.
