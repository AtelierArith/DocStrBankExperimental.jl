```julia
DDVFA(
    opts::AdaptiveResonance.opts_DDVFA
) -> AdaptiveResonance.DDVFA

```

# Summary

Implements a DDVFA learner with specified options.

# Arguments

  * `opts::opts_DDVFA`: the DDVFA options (see [`AdaptiveResonance.opts_DDVFA`](@ref)).

# Examples

```julia-repl
julia> my_opts = opts_DDVFA()
julia> DDVFA(my_opts)
DDVFA
    opts: opts_DDVFA
    subopts: opts_FuzzyART
    ...
```

# Method List / Definition Locations

```julia
DDVFA(opts)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:227`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl).
