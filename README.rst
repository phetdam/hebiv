.. README for c_numpy_demo

hebiv
=====

*We should forget about small efficiencies, say about 97% of the time: premature
optimization is the root of all evil* [#]_

A multithreaded Python package for computing option implied volatilities.

Migration in progress.

Includes a demo script [#]_ that performs a comparison of execution speed for
the iterative computation of Black and Bachelier implied volatility using
Halley's and Newton's methods. The script compares the time taken to solve the
Black and Bachelier implied volatilities of ~1 million European option prices
for a pure Python implementation using `scipy.optimize.newton`__, a mixed 
implementation where a minimalistic C implementation of Halley's/Newton's method
is used to solve for the price but iteration through prices is still done in
Python, and a ``ctypes`` wrapped pure C implementation. The script illustrates
the difference in speed between converting data types and looping directly in C
versus iterating through the prices in Python and using ``ctypes`` to call the C
function for each price [#]_.

There is a small test suite that can be run with pytest__ after installation.

.. [#] Attributed to Sir Tony Hoare, popularized by Donald Knuth.

.. [#] This does not exist yet.

.. [#] Should include a demo of how multithreading helps with large inputs.

.. __: https://docs.scipy.org/doc/scipy/reference/generated/scipy.optimize.
   newton.html

.. __: https://docs.pytest.org/en/stable/contents.html

Installation
------------

   Note:

   The following sections are out of date and foremly from the `c_npy_demo`__
   ``README.rst``. They will change in the future.

.. __: https://github.com/phetdam/c_npy_demo

From source
~~~~~~~~~~~

Building from this (unstable) repo will probably only work on Linux systems.
Local extension builds are done on WSL Ubuntu 18.04 with gcc 9.3 while builds on
Travis CI virtual machines are done on Ubuntu 18.04 with gcc 7.4. There is also
an implicit dependency on the gcc version being high enough such that an OpenMP
implementation is included [#]_. For example, I have ``libgomp.so.1.0.0`` in
``/usr/lib/x86_64-linux-gnu/``, with appropriate symbolic links.

.. [#] Fun exercise: Find where I have (sparingly) used OpenMP directives.

From PyPI
~~~~~~~~~

Although this package is not on PyPI (yet), I have successfully built
``manylinux1`` wheels using Travis CI on the ``manylinux1`` Docker images
provided by PyPA, of which more information can be found at the
`manylinux GitHub`__.

.. __: https://github.com/pypa/manylinux

Contents
--------

TBA. Currently looks like some pure Python code, ``pytest`` test suite,
demo module to run benchmarks, separate C shared library for implied volatility
calculations, and a Python extension module written in C.

Documentation
-------------

In progress, and will be eventually be hosted on `Read the Docs`__. For now,
the ``doc`` directory probably only has ``conf.py`` and ``index.rst``.

.. __: https://readthedocs.org/