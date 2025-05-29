# ODEInterface

This julia module provides an interface to solvers for ordinary differential equations (ODEs) written in Fortran for solving initial value problems of the form

```
x' = rhs(t,x),      x(t₀) = x₀
```

or (for solvers supporting a "mass matrix" M)

```
M⋅x' = rhs(t,x),    x(t₀) = x₀.
```

## What does "Interface" mean?

This julia module does *not* contain code for solving initial value problems, but this module does contain code for interacting with compiled Fortran-solvers. That's the reason, why this module is not called ODESuite.

## What solvers are currently supported?

Currently the following Fortran-solvers, written by Prof. E. Hairer and Prof. G. Wanner, are supported:

  * dopri5: explicit Runge-Kutta method of order 5(4) due to Dormand & Prince
  * dop853: explicit Runge-Kutta method of order 8(5,3) due to Dormand & Prince
  * odex: GBS extrapolation-algorithm based on the explicit midpoint rule
  * radau5: implicit Runge-Kutta method (Radau IIA) of order 5
  * radau: implicit Runge-Kutta method (Radau IIA) of variable order between 5 and 13
  * seulex: extrapolation-algorithm based on the linear implicit Euler method
  * rodas: Rosenbrock method of order 4(3) (with possibly singular mass matrix)

see [Software page of Prof. Hairer](http://www.unige.ch/~hairer/software.html).

Additionally the following Fortran-solvers from the [SLATEC Common Mathematical Library](http://www.netlib.org/slatec/) are supported:

  * ddeabm: Adams-Bashforth-Moulton Predictor-Corrector method (order between 1 and 12)
  * ddebdf: Backward Differentiation Formula (orders between 1 and 5)

The following features of this solvers are supported by this ODEInterface:

  * providing an output function (e.g. for dense output or for event location) to the solvers
  * providing mass- and jacobi-matrices for the solvers (with support for banded matrices)
  * all the solvers' parameters for fine-tuning them
  * support for problems with "special structure", see `help_specialstructure`

Also supported:

  * bvpsol: a boundary value problem solver for highly nonlinear two point boundary value problems using either a local linear solver or a global sparse linear solver. **Please note: The license for `bvpsol` only covers non commercial use, see [License](./LICENSE.md).** written by P. Deuflhard, G. Bader, L. Weimann, see [CodeLib at ZIB](http://elib.zib.de/pub/elib/codelib/en/bvpode.html).
  * colnew: a multi-point boundary value problem solver for mixed order systems using collocation. Written by U. Ascher, G. Bader, see [Colnew Homepage](https://people.sc.fsu.edu/~jburkardt/f77_src/colnew/colnew.html).
  * BVP*M-2: a boundary value problem solver for the numerical solution of boundary value ordinary differential equations with defect and global error control. Written by J. J. Boisvert, P.H. Muir and R. J. Spiteri, see [BVP*M-2 Page](http://cs.stmarys.ca/~muir/BVP*SOLVER*Webpage.shtml).

## What are the requirements for this module

In order to use this module, you have to *compile* the supported Fortran solvers and provide a shared library for each solver. The build-script of this module tries to compile all solvers automatically. But you can use your own compiled versions (with different compile-time options or compilers). Just call `ODEInterface.help_solversupport` for further informations (help topics) on how to compile the solvers and how to create shared libraries.

## Further help

see `ODEInterface.help_overview` for an overview of some help topics.

## Contacting the author of this module

The author of this julia module is

```
 Dr. Christian Ludwig
 email: ludwig@ma.tum.de
   (Faculty of Mathematics, Technische Universität München)
```
