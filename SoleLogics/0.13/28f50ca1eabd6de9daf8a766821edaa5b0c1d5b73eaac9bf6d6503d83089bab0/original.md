```
struct Point{N,T<:Real} <: GeometricalWorld
    xyz :: NTuple{N,T}
end
```

A point in an `N`-dimensional space, with integer coordinates.

# Examples

```julia-repl
julia> SoleLogics.goeswithdim(SoleLogics.Point(1,2,3),3)
true

julia> SoleLogics.goeswithdim(SoleLogics.Point(1,2,3),2)
false

```

See also [`goeswithdim`](@ref), [`Interval`](@ref), [`Interval2D`](@ref), [`GeometricalWorld`](@ref), [`AbstractWorld`](@ref).
