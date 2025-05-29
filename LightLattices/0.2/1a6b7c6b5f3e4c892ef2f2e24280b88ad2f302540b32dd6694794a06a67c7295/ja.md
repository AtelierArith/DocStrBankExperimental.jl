```julia
struct HomogeneousCell{D, T, L<:Union{Nothing, Symbol}} <: LightLattices.AbstractCell{D, T}
```

  * `cell_vectors::Array{StaticArraysCore.SVector{D, T}, 1} where {D, T}`: ノードの座標。
  * `label::Union{Nothing, Symbol}`: セルのラベル。

`D`次元空間における無秩序な均質ノードのコレクション。
