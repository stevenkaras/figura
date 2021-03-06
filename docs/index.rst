.. Figura documentation master file, created by
   sphinx-quickstart on Wed May 25 18:40:18 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

==================================
FIGURA
==================================

.. toctree::
   :maxdepth: 1

What is Figura?
==================

Figura is an *expressive high-level configuration language* based on Python syntax.

The Zen of Figura
==================

#. **Config files are code**.  They need to be designed.  Think OOD.
#. You should never have to repeat yourself.
#. Config-using code (code referencing config values and using them) should be decoupled from config code.
#. Config-using code should be simple.

Getting Started
==================================

Installation
-----------------

Install the `python package <figura.html>`_ using ``pip``::

    % pip install figura
    
This also installs the ``figura_print`` executable script for parsing Figura configuration files.

Hello World!
--------------------

The package comes with a ready-to-use "hello_world.fig" configuration file::

    % cat hello_world.fig
    """ A sample Figura configuration file for greeting The World! """
    class greeting:
        format = 'Hello, %s!'
        greetee = 'World'

After parsing it, the raw config (in JSON form) looks like this::

    % figura_print figura.hello_world
    {
      "greeting": {
        "greetee": "World", 
        "format": "Hello, %s!"
      }
    }

A sample Python snippet for printing the greeting::

   from figura import read_config
   greeting_config = read_config('figura.hello_world').greeting
   print(greeting_config.format % greeting_config.greetee)
   #  =>  Hello, World!

Python Importability
---------------------

Every figura configuration file is a python module. When the file is processed,
the python interpreter is used to first import the module. This means that in order for the
python interpreter to find the modules, ``PYTHONPATH`` needs to be set accordingly.

In a \*nix system (using ``bash``), you can set PYTHONPATH like this::

    export PYTHONPATH=/PATH/TO/FIGURA/docs/guide/

Also, the directory (and subdirectories) containing Figura files must contain
a ``__init__.fig`` file. This is required for the same reason --
to make the modules python-importable.

File Extension
---------------------

In Figura V1.x.x, we use by defualt the standard python ".py" file extension for Figura
config files.  In V1.1.0 support was added for using other file extensions, in order to
distinguish python scripts and modules from Figura config files.

In Figura version 2 (not yet released) the default extension will be ".fig".  Users using
Figura version>=1.1.0 are encouraged to use Figura in a forward-compatible way, by switching
the extension explicitly to ".fig". This is done by running::

    # Run this once, before reading any figura files:
    from figura.settings import set_extension_fig; set_extension_fig()


Documentation
==================================

For an easy start, check out the `Tutorial <tutorial.html>`_ and `Reference Guide <guide.html>`_.

A discussion about the `pros and cons <proscons.html>`_ of the Figura language.

Also refer to the documentation of the `Figura Python package <figura.html>`_.


Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

Other locations
==================

- `Figura's GitHub page <https://github.com/shx2/figura>`_
- `Figura on PyPI <https://pypi.python.org/pypi?:action=display&name=figura>`_
- `Figura on ReadTheDocs <https://figura.readthedocs.io/en/latest/index.html>`_ (this page)
