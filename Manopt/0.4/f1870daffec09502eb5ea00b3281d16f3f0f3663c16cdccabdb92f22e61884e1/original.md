```
Stepsize
```

An abstract type for the functors representing step sizes. These are callable structures. The naming scheme is `TypeOfStepSize`, for example `ConstantStepsize`.

Every Stepsize has to provide a constructor and its function has to have the interface `(p,o,i)` where a [`AbstractManoptProblem`](@ref) as well as [`AbstractManoptSolverState`](@ref) and the current number of iterations are the arguments and returns a number, namely the stepsize to use.

# See also

[`Linesearch`](@ref)
