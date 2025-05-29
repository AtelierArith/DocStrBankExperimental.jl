```
CoupledODEs <: ContinuousTimeDynamicalSystem
CoupledODEs(f, u0 [, p]; diffeq, t0 = 0.0)
```

A deterministic continuous time dynamical system defined by a set of coupled ordinary differential equations as follows:

$$
\frac{d\vec{u}}{dt} = \vec{f}(\vec{u}, p, t)
$$

An alias for `CoupledODE` is `ContinuousDynamicalSystem`.

Optionally provide the parameter container `p` and initial time as keyword `t0`.

For construction instructions regarding `f, u0` see the DynamicalSystems.jl tutorial.

## DifferentialEquations.jl interfacing

The ODEs are evolved via the solvers of DifferentialEquations.jl. When initializing a `CoupledODEs`, you can specify the solver that will integrate `f` in time, along with any other integration options, using the `diffeq` keyword. For example you could use `diffeq = (abstol = 1e-9, reltol = 1e-9)`. If you want to specify a solver, do so by using the keyword `alg`, e.g.: `diffeq = (alg = Tsit5(), reltol = 1e-6)`. This requires you to have been first `using OrdinaryDiffEq` (or smaller library package such as `OrdinaryDiffEqVerner`) to access the solvers. The default `diffeq` is:

(alg = OrdinaryDiffEqTsit5.Tsit5{typeof(OrdinaryDiffEqCore.trivial*limiter!), typeof(OrdinaryDiffEqCore.trivial*limiter!), Static.False}(OrdinaryDiffEqCore.trivial*limiter!, OrdinaryDiffEqCore.trivial*limiter!, static(false)), abstol = 1.0e-6, reltol = 1.0e-6)

`diffeq` keywords can also include `callback` for [event handling ](http://docs.juliadiffeq.org/latest/features/callback_functions.html).

The convenience constructors `CoupledODEs(prob::ODEProblem [, diffeq])` and `CoupledODEs(ds::CoupledODEs [, diffeq])` are also available. Use `ODEProblem(ds::CoupledODEs, tspan = (t0, Inf))` to obtain the problem.

To integrate with ModelingToolkit.jl, the dynamical system **must** be created via the `ODEProblem` (which itself is created via ModelingToolkit.jl), see the Tutorial for an example.

Dev note: `CoupledODEs` is a light wrapper of `ODEIntegrator` from DifferentialEquations.jl.
