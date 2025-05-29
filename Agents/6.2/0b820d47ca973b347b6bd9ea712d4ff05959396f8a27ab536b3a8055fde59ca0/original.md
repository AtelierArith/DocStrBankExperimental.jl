```
GridSpaceSingle(d::NTuple{D, Int}; periodic = true, metric = :chebyshev)
```

This is a specialized version of [`GridSpace`](@ref) that allows only one agent per position, and utilizes this knowledge to offer significant performance gains versus [`GridSpace`](@ref).

This space **reserves agent ID = 0 for internal usage.** Agents should be initialized with non-zero IDs, either positive or negative. This is not checked internally.

All arguments and keywords behave exactly as in [`GridSpace`](@ref).
