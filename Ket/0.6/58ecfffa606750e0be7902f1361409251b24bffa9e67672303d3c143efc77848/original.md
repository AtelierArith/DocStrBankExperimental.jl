```
entanglement_robustness(
    ρ::AbstractMatrix{T},
    dims::AbstractVecOrTuple = _equal_sizes(ρ),
    n::Integer = 1;
    noise::String = "white"
    ppt::Bool = true,
    inner::Bool = false,
    verbose::Bool = false,
    dualize::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Lower (or upper) bounds the entanglement robustness of state `ρ` with subsystem dimensions `dims` using level `n` of the DPS hierarchy (or inner DPS, when `inner = true`). Argument `noise` indicates the kind of noise to be used: "white" (default), "separable", or "general". Argument `ppt` indicates whether to include the partial transposition constraints. Argument `dualize` determines whether the dual problem is solved instead. WARNING: This is critical for performance, and the correct choice depends on the solver.

Returns the robustness and a witness W (note that for `inner = true`, this might not be a valid entanglement witness).
