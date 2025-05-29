```
MultiScaleSkipDeepEquilibriumNetwork(main_layers::Tuple, mapping_layers::Matrix,
    post_fuse_layer::Union{Nothing, Tuple}, [init = nothing,] solver,
    scales::NTuple{N, NTuple{L, Int64}}; kwargs...)
```

Skip Multi Scale Deep Equilibrium Network as proposed in [pal2022mixing](@cite). Alias which creates a [`MultiScaleDeepEquilibriumNetwork`](@ref) with `init` kwarg set to passed value.

If `init` is not passed, it creates a MultiScale Regularized Deep Equilibrium Network.
