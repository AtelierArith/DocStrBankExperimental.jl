```julia
FuzzyART(; kwargs...) -> AdaptiveResonance.FuzzyART

```

# Summary

Implements a Fuzzy ART learner with optional keyword arguments.

# Arguments

  * `kwargs`: keyword arguments of FuzzyART options (see [`AdaptiveResonance.opts_FuzzyART`](@ref)).

# Examples

By default:

```julia-repl
julia> FuzzyART()
FuzzyART
    opts: opts_FuzzyART
    ...
```

or with keyword arguments:

```julia-repl
julia> FuzzyART(rho=0.7)
FuzzyART
    opts: opts_FuzzyART
    ...
```

# Method List / Definition Locations

```julia
FuzzyART(; kwargs...)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl:192`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ART/single/modules/FuzzyART.jl).
