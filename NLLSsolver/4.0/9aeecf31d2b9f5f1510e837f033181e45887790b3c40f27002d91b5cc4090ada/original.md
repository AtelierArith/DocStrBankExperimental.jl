```
NLLSsolver.CostTrajectory
```

A type with the fields

```julia
    costs::Vector{Float64}
    times_ns::Vector{UInt64}
    trajectory::Vector{Vector{Float64}}
```

that can be used to store per iteration optimization information.

---

```julia
    CostTrajectory()
```

Construct an empty `CostTrajectory` struct, ready for use with [`storecostscallback`](@ref).
