```julia
opts_GammaNormalizedFuzzyART(; kwargs...)

```

# Summary

Implements a Gamma-Normalized FuzzyART module's options.

GammaNormalizedFuzzyART is a variant of [`FuzzyART`](@ref), using the [`AdaptiveResonance.opts_FuzzyART`](@ref) options. This constructor passes `gamma_normalization=true`, which internally uses `match=:gamma_match` and `activation=:gamma_activation` in addition to the keyword argument options you provide.

These options are a [`Parameters.jl`](https://github.com/mauro3/Parameters.jl) struct, taking custom options keyword arguments. Each field has a default value listed below.

# Method List / Definition Locations

```julia
opts_GammaNormalizedFuzzyART(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/variants.jl:50`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/variants.jl).
