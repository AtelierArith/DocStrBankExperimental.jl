```
titr = TileIterator(axes::NTuple{N, AbstractUnitRange}, strategy)
```

`axes`を`strategy`に従って小さな軸のイテレータ`titr`に分解します。

`strategy`引数はタイルの詳細を制御します。たとえば、軸の長さがタイルサイズで割り切れない場合、何が起こるべきでしょうか？1つのアプローチは、最後のタイルのサイズ要件を緩和することです。もう1つの可能性は、すべてのタイルが要求されたサイズになるように`stride`を緩和することですが、タイルがわずかに重なる可能性があります。これら2つの可能性は[`RelaxLastTile`](@ref)と[`RelaxStride`](@ref)によって実装されています。

# 例

```jldoctest
julia> using TiledIteration

julia> collect(TileIterator((1:3, 0:5), RelaxLastTile((2, 3))))
2×2 Array{Tuple{UnitRange{Int64},UnitRange{Int64}},2}:
 (1:2, 0:2)  (1:2, 3:5)
 (3:3, 0:2)  (3:3, 3:5)

julia> collect(TileIterator((1:3, 0:5), (2, 3))) # defaults to RelaxLastTile
2×2 Array{Tuple{UnitRange{Int64},UnitRange{Int64}},2}:
 (1:2, 0:2)  (1:2, 3:5)
 (3:3, 0:2)  (3:3, 3:5)

julia> collect(TileIterator((1:3, 0:5), RelaxStride((2, 3))))
2×2 Array{Tuple{UnitRange{Int64},UnitRange{Int64}},2}:
 (1:2, 0:2)  (1:2, 3:5)
 (2:3, 0:2)  (2:3, 3:5)
```
