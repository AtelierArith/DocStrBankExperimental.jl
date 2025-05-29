```julia
mutable struct ILMSystem{static, PT, N, PHT, BCF, FF, DTF, MTF, BCT, ECT}
```

A system of operators and caches for immersed layer problems. This is constructed by [`construct_system`](@ref)
