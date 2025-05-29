```julia
DAM(
    opts::AdaptiveResonance.opts_SFAM
) -> AdaptiveResonance.SFAM

```

# Summary

Implements a Default ARTMAP module with specified options.

Default ARTMAP is a variant of SFAM, using the [`AdaptiveResonance.opts_SFAM`](@ref) options. This constructor sets the activation to `:choice_by_difference` in addition to the keyword argument options you provide.

# Arguments

  * `opts::opts_SFAM`: the Simplified FuzzyARTMAP options (see [`AdaptiveResonance.opts_SFAM`](@ref)).

# Method List / Definition Locations

```julia
DAM(opts)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl:41`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/variants.jl).
