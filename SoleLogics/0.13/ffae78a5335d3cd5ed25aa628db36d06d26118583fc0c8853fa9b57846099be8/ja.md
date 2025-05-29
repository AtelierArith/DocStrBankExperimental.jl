```
struct FullDimensionalFrame{N,W<:AbstractWorld} <: AbstractDimensionalFrame{N,W}
    channelsize::NTuple{N,Int}
end
```

全次元フレームの抽象型。サイズが (X, Y, Z, ...) の `N` 次元配列に対して、対応する全次元フレームは、空間内の各 M-ハイパーレクタングルに対して正確に1つの頂点があるグラフです (1:X, 1:Y, 1:Z, ...)、ここで `M ≤ N` です。

ここで、`M`-ハイパーレクタングルは、[`Point`](@ref) であるか、または区間の `N`-タプル（例: [`Interval`](@ref) または [`Interval2D`](@ref)）であり、各区間は自然数のペア (x,y) で次の条件を満たします: i) x > 0; ii) y > 0; iii) x < y。

現在の実装は N ∈ {0,1,2} を処理できます。

# 例

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

さらに [`OneWorld`](@ref), [`Interval`](@ref), [`Interval2D`](@ref), [`IntervalRelation`](@ref), [`RectangleRelation`](@ref), [`accessibles`](@ref), [`AbstractDimensionalFrame`](@ref), [`AbstractMultiModalFrame`](@ref) を参照してください。
