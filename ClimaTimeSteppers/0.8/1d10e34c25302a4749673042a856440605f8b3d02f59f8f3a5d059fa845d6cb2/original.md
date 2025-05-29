```
ConvergenceChecker(;
    norm_condition,
    component_condition,
    condition_combiner,
    norm = LinearAlgebra.norm,
)
```

Checks whether a sequence `val[0], val[1], val[2], ...` has converged to some limit `L`, given the errors `err[iter] = val[iter] .- L`. This is done by calling `is_converged!(::ConvergenceChecker, cache, val, err, iter)`, where `val = val[iter]` and `err = err[iter]`. If the value of `L` is not known, `err` can be an approximation of `err[iter]`. The `cache` for a `ConvergenceChecker` can be obtained with `allocate_cache(::ConvergenceChecker, val_prototype)`, where `val_prototype` is `similar` to `val` and `err`.

A `ConvergenceChecker` can perform two types of checks–-it can check whether `norm(val)` and `norm(err)` satisfy some `ConvergenceCondition`, and it can check whether all the components of `abs.(val)` and `abs.(err)` individually satisfy some `ConvergenceCondition`. These two checks can be combined with either `&` or `|`. If one of the checks is not needed, the corresponding `ConvergenceCondition` can be set to `nothing`.

Instead of `LinearAlgebra.norm`, `norm` can be set to anything that will convert `val` and `err` to non-negative scalar values.
