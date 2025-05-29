```julia
DVFA(; kwargs...) -> AdaptiveResonance.DVFA

```

# Summary

Implements a DVFA learner with optional keyword arguments.

# Arguments

  * `kwargs`: keyword arguments to pass to the DVFA options struct (see [`AdaptiveResonance.opts_DVFA`](@ref).)

# Examples

By default:

```julia-repl
julia> DVFA()
DVFA
    opts: opts_DVFA
    ...
```

or with keyword arguments:

```julia-repl
julia> DVFA(rho=0.7)
DVFA
    opts: opts_DVFA
    ...
```

# Method List / Definition Locations

```julia
DVFA(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl:189`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/DVFA.jl).
