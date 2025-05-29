```julia
SFAM(; kwargs...) -> AdaptiveResonance.SFAM

```

# Summary

Implements a Simple Fuzzy ARTMAP learner with optional keyword arguments.

# Arguments

  * `kwargs`: keyword arguments to pass to the Simple Fuzzy ARTMAP options struct (see [`AdaptiveResonance.opts_SFAM`](@ref).)

# Examples

By default:

```julia-repl
julia> SFAM()
SFAM
    opts: opts_SFAM
    ...
```

or with keyword arguments:

```julia-repl
julia> SFAM(rho=0.6)
SFAM
    opts: opts_SFAM
    ...
```

# Method List / Definition Locations

```julia
SFAM(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl:166`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/SFAM.jl).
