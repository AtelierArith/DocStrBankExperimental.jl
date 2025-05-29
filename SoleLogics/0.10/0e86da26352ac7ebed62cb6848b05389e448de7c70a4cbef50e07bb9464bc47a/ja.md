```
struct Interval2D{T} <: GeometricalWorld
    x :: Interval{T}
    y :: Interval{T}
end
```

2次元空間における直交矩形で、型 `T` の座標を持ちます。これは2次元の `Interval` の対応物であり、2つの直交する `Interval` の組み合わせです。

# 例

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

他の参照としては [`goeswithdim`](@ref), [`accessibles`](@ref), [`FullDimensionalFrame`](@ref), [`Point`](@ref), [`Interval`](@ref), [`GeometricalWorld`](@ref), [`AbstractWorld`](@ref) があります。
