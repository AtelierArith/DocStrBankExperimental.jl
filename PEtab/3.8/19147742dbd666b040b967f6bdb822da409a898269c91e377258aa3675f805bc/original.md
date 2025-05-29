```
remake(prob::PEtabODEProblem, xchange::Dict)::PEtabODEProblem
```

Fix and consequently remove a set of parameters from being estimated without rebuilding `prob`.

`xchange` should be provided as a `Dict` with parameter names and their new values. For example, to fix `k1` to `1.0`, provide `xchange = Dict(:k1 => 1.0)`. The parameters to be fixed can only be those that were originally set to be estimated.

`remake` is the most efficient approach for fixing parameters, as it does not re-compile the problem.
