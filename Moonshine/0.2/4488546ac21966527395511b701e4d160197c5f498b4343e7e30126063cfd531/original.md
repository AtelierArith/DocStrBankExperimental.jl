```julia
struct AncestralIntervals{T<:(AbstractVector{<:IntervalSets.AbstractInterval})} <: AbstractVector{IntervalSets.AbstractInterval}
```

Collection of intervals.

Meant to represent the set of intervals an edge/vertex is ancestral for. You might want to use the convenient shorthand [`AIs`](@ref) instead.

Implements [the iteration interface](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-iteration) and [the array interface](https://docs.julialang.org/en/v1/manual/interfaces/#man-interface-array).

See also [`AI`](@ref) and [`Ω`](@ref).

# Fields

  * `data::AbstractVector{<:IntervalSets.AbstractInterval}`

# Constructors

```julia
AncestralIntervals(data; simplify)
```

defined at [`packages/Moonshine/7JVTP/src/AncestralIntervals.jl:78`](file:///Users/atelierarith/.julia/packages/Moonshine/7JVTP/src/AncestralIntervals.jl).

# Arguments

If `simplify = true`, intervals contained in data are simplified: see [`simplify!`](@ref) for details.

!!! warning
    Many methods assume `AIs` to be simplified. You might want to disable simplification to optimize a sequence of operation, but you should probably simplify the final result.

