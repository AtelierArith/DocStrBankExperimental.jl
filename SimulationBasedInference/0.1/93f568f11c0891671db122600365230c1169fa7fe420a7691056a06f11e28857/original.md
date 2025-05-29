```
SimulatorForwardProblem{probType,obsType,configType,names} <: SciMLBase.AbstractSciMLProblem
```

Represents a "forward" problem from parameters/initial conditions to output `SimulatorObservable`s. This type wraps an underlying `SciMLProblem`, a set of `Observable`s, and an optional, probelm-dependent configuration type.

```
SimulatorForwardProblem(prob::SciMLBase.AbstractSciMLProblem, observables::SimulatorObservable...)
```

Constructs a generic simulator forward problem from the given `AbstractSciMLProblem`; note that this could be any problem type, e.g. an optimization problem, nonlinear system, quadrature, etc.

```
SimulatorForwardProblem(f, p0::AbstractVector, observables::SimulatorObservable...)
```

Creates a forward problem from the given function or callable type `f` with initial parameters `p0` and the given `observables`.

```
SimulatorForwardProblem(f, p0::AbstractVector)
```

Creates a forward problem from the given function or callable type `f` with initial parameters `p0` and a default transient observable. Note that this constructor calls `f(p0)` in order to determine the shape of the observable. If `f` is very costly and this is undesirable, it is recommended to use the explicit constructor.
