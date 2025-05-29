```
struct Point{N,T<:Real} <: GeometricalWorld
    xyz :: NTuple{N,T}
end
```

整数座標を持つ `N` 次元空間の点。

# 例

```julia-repl
julia> SoleLogics.goeswithdim(SoleLogics.Point(1,2,3),3)
true

julia> SoleLogics.goeswithdim(SoleLogics.Point(1,2,3),2)
false

```

関連項目 [`goeswithdim`](@ref), [`Interval`](@ref), [`Interval2D`](@ref), [`GeometricalWorld`](@ref), [`AbstractWorld`](@ref).
