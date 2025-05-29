```julia
SFAM(
    opts::AdaptiveResonance.opts_SFAM
) -> AdaptiveResonance.SFAM

```

# Summary

Implements a Simple Fuzzy ARTMAP learner with specified options.

# Arguments

  * `opts::opts_SFAM`: the Simple Fuzzy ARTMAP options (see [`AdaptiveResonance.opts_SFAM`](@ref)).

# Examples

```julia-repl
julia> opts = opts_SFAM()
julia> SFAM(opts)
SFAM
    opts: opts_SFAM
    ...
```

# Method List / Definition Locations

```julia
SFAM(opts)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:186`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl).
