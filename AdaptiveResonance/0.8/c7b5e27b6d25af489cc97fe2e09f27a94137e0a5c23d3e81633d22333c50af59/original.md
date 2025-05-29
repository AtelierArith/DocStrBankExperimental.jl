```julia
DVFA(
    opts::AdaptiveResonance.opts_DVFA
) -> AdaptiveResonance.DVFA

```

# Summary

Implements a DVFA learner with specified options.

# Arguments

  * `opts::opts_DVFA`: the DVFA options (see [`AdaptiveResonance.opts_DVFA`](@ref)).

# Examples

```julia-repl
julia> my_opts = opts_DVFA()
julia> DVFA(my_opts)
DVFA
    opts: opts_DVFA
    ...
```

# Method List / Definition Locations

```julia
DVFA(opts)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:209`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl).
