```julia
GammaNormalizedFuzzyART(
;
    kwargs...
) -> AdaptiveResonance.FuzzyART

```

# Summary

Constructs a Gamma-Normalized FuzzyART module as a variant of FuzzyART by using the gamma_normalization option.

GammaNormalizedFuzzyART is a variant of [`FuzzyART`](@ref), using the [`AdaptiveResonance.opts_FuzzyART`](@ref) options. This constructor passes `gamma_normalization=true`, which internally uses `match=:gamma_match` and `activation=:gamma_activation` in addition to the keyword argument options you provide.

# Arguments

  * `kwargs`: keyword arguments of FuzzyART options (see [`AdaptiveResonance.opts_FuzzyART`](@ref))

# Method List / Definition Locations

```julia
GammaNormalizedFuzzyART(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/variants.jl:26`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/variants.jl).
