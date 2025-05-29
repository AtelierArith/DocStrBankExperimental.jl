```julia
DDVFA(; kwargs...) -> AdaptiveResonance.DDVFA

```

# Summary

Implements a DDVFA learner with optional keyword arguments.

# Arguments

  * `kwargs`: keyword arguments to pass to the DDVFA options struct (see [`AdaptiveResonance.opts_DDVFA`](@ref).)

# Examples

By default:

```julia-repl
julia> DDVFA()
DDVFA
    opts: opts_DDVFA
    subopts: opts_FuzzyART
    ...
```

or with keyword arguments:

```julia-repl
julia> DDVFA(rho_lb=0.4, rho_ub = 0.75)
DDVFA
    opts: opts_DDVFA
    subopts: opts_FuzzyART
    ...
```

# Method List / Definition Locations

```julia
DDVFA(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl:206`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/distributed/modules/DDVFA.jl).
