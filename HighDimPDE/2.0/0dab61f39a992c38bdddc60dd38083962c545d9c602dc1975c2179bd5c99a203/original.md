```julia
solve(
    prob::Union{HighDimPDE.PIDEProblem, HighDimPDE.ParabolicPDEProblem},
    alg::HighDimPDE.MLP;
    multithreading,
    verbose
) -> HighDimPDE.PIDESolution{_A, _B, Nothing, _C, Nothing, Nothing} where {_A, _B, _C}

```

Returns a `PIDESolution` object.

# Arguments

  * `multithreading` : if `true`, distributes the job over all the threads available.
  * `verbose`: print information over the iterations.
