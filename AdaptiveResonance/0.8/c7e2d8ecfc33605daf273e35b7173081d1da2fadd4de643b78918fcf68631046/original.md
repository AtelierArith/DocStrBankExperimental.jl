```julia
FAM(; kwargs...) -> AdaptiveResonance.FAM

```

# Summary

Implements a Fuzzy ARTMAP learner with optional keyword arguments.

# Examples

By default:

```julia-repl
julia> FAM()
FAM
    opts: opts_FAM
    ...
```

or with keyword arguments:

```julia-repl
julia> FAM(rho=0.7)
FAM
    opts: opts_FAM
    ...
```

# Method List / Definition Locations

```julia
FAM(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/FAM.jl:129`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/FAM.jl).
