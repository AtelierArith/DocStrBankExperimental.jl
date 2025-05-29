```
bbsetup(problem[; parameters::Associative, kwargs...])
```

Set up optimization method for a given problem.

See `setup_problem()` for the types of `problem` supported. The optimization method parameters could be specified via `kwargs` or `parameters` arguments.

Returns the initialized `OptController` instance. To actually run the method call `bboptimize()` or `run!()`.

See also [BlackBoxOptim.OptRunController](@ref) for a full list of supported parameters.
