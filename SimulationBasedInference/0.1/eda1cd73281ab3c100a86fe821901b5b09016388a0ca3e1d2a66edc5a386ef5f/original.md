```
SimulatorForwardProblem(f, p0::AbstractVector, observables::SimulatorObservable...)
```

Constructs a `SimulatorForwardProblem` from the callable/function `f(x)` and observables. The base problem will be a `SimpleForwardProblem` which wraps `f(x)` and uses `p0` as the default parameter/input values for `x`.
