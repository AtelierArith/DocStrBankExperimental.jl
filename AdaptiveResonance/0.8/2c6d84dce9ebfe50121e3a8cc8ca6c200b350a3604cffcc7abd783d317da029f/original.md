```julia
opts_DAM(; kwargs...) -> AdaptiveResonance.opts_SFAM

```

# Summary

Implements a Default ARTMAP module's options.

Default ARTMAP is a variant of SFAM, using the [`AdaptiveResonance.opts_SFAM`](@ref) options. This constructor sets the activation to `:choice_by_difference` in addition to the keyword argument options you provide.

These options are a [`Parameters.jl`](https://github.com/mauro3/Parameters.jl) struct, taking custom options keyword arguments. Each field has a default value listed below.

# Method List / Definition Locations

```julia
opts_DAM(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl:52`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl).
