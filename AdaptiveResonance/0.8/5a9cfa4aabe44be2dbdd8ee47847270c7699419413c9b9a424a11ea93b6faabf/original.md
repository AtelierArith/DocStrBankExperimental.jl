```julia
GammaNormalizedFuzzyART(
    opts::AdaptiveResonance.opts_FuzzyART
)

```

# Summary

Implements a Gamma-Normalized FuzzyART module with specified options.

GammaNormalizedFuzzyART is a variant of [`FuzzyART`](@ref), using the [`AdaptiveResonance.opts_FuzzyART`](@ref) options. This constructor passes `gamma_normalization=true`, which internally uses `match=:gamma_match` and `activation=:gamma_activation` in addition to the keyword argument options you provide.

# Arguments

  * `opts::opts_FuzzyART`: the Fuzzy ART options (see [`AdaptiveResonance.opts_FuzzyART`](@ref)).

# Method List / Definition Locations

```julia
GammaNormalizedFuzzyART(opts)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/variants.jl:39`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/variants.jl).
