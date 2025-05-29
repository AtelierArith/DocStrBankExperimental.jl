```
exact_penalty_method!(M, f, grad_f, p; kwargs...)
exact_penalty_method!(M, cmo::ConstrainedManifoldObjective, p; kwargs...)
```

perform the exact penalty method (EPM) performed in place of `p`.

For all options, see [`exact_penalty_method`](@ref).
