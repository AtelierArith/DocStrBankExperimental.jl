```
struct Interval{T} <: GeometricalWorld
    x :: T
    y :: T
end
```

1次元空間における区間で、型 `T` の座標を持ちます。

# 例

```julia-repl
julia> SoleLogics.goeswithdim(SoleLogics.Interval(1,2),1)
true

julia> SoleLogics.goeswithdim(SoleLogics.Interval(1,2),2)
false

julia> collect(accessibles(SoleLogics.FullDimensionalFrame(5), Interval(1,2), SoleLogics.IA_L))
6-element Vector{Interval{Int64}}:
 (3−4)
 (3−5)
 (4−5)
 (3−6)
 (4−6)
 (5−6)


```

関連項目として [`goeswithdim`](@ref), [`accessibles`](@ref), [`FullDimensionalFrame`](@ref), [`Point`](@ref), [`Interval2D`](@ref), [`GeometricalWorld`](@ref), [`AbstractWorld`](@ref) を参照してください。
