```julia
struct SingleMultiEdge{T<:Integer} <: Graphs.SimpleGraphs.AbstractSimpleEdge{T<:Integer}
```

  * `src::Integer`: ソースノード
  * `dst::Integer`: デスティネーションノード
  * `m::Integer`: エッジの重複度

`src` と `dst` を接続するエッジの `m` 番目のインスタンス。
