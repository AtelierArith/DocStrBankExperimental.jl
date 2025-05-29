```
struct Interval2D{T<:Real} <: GeometricalWorld
    x :: Interval{T}
    y :: Interval{T}
end
```

A orthogonal rectangle in a 2-dimensional space, with coordinates of type `T`. This is the 2-dimensional `Interval` counterpart, that is, the combination of two orthogonal `Interval`s.

# Examples

```julia-repl
julia> SoleLogics.goeswithdim(SoleLogics.Interval2D((1,2),(3,4)),1)
false

julia> SoleLogics.goeswithdim(SoleLogics.Interval2D((1,2),(3,4)),2)
true

julia> collect(accessibles(SoleLogics.FullDimensionalFrame(5,5), Interval2D((2,3),(2,4)), SoleLogics.IA_LL))
3-element Vector{Interval2D{Int64}}:
 ((4−5)×(5−6))
 ((4−6)×(5−6))
 ((5−6)×(5−6))

```

See also [`goeswithdim`](@ref), [`accessibles`](@ref), [`FullDimensionalFrame`](@ref), [`Point`](@ref), [`Interval`](@ref), [`GeometricalWorld`](@ref), [`AbstractWorld`](@ref).
