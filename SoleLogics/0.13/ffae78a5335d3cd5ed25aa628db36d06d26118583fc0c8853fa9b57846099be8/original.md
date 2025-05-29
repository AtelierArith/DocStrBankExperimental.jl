```
struct FullDimensionalFrame{N,W<:AbstractWorld} <: AbstractDimensionalFrame{N,W}
    channelsize::NTuple{N,Int}
end
```

Abstract type for full dimensional frames. Given a `N`-dimensional array of size (X, Y, Z, ...) the corresponding full dimensional frame is a graph where there is exactly one vertex for each M-hyperrectangle in the space (1:X, 1:Y, 1:Z, ...), with `M ≤ N`.

Here, the `M`-hyperrectangle can be either a [`Point`](@ref), or a `N`-tuple of intervals (e.g., [`Interval`](@ref) or [`Interval2D`](@ref)), where each interval is a pair of natural numbers (x,y) where: i) x > 0; ii) y > 0; iii) x < y.

The current implementation can handle N ∈ {0,1,2}.

# Examples

```julia-repl
julia> SoleLogics.allworlds(SoleLogics.FullDimensionalFrame((),))
1-element Vector{OneWorld}:
 −

julia> nworlds(SoleLogics.FullDimensionalFrame((10,), Interval{Int}))
55

julia> nworlds(SoleLogics.FullDimensionalFrame((10,10),))
3025

julia> collect(accessibles(SoleLogics.FullDimensionalFrame(5,5), Interval2D((2,3),(2,4)), SoleLogics.IA_LL))
3-element Vector{Interval2D{Int64}}:
 ((4−5)×(5−6))
 ((4−6)×(5−6))
 ((5−6)×(5−6))

```

See also [`OneWorld`](@ref), [`Interval`](@ref), [`Interval2D`](@ref), [`IntervalRelation`](@ref), [`RectangleRelation`](@ref), [`accessibles`](@ref), [`AbstractDimensionalFrame`](@ref), [`AbstractMultiModalFrame`](@ref).
