```julia
struct InhomogeneousCell{D, T, N, L<:Union{Nothing, Symbol}, T′} <: LightLattices.AbstractCell{D, T}
```

  * `cell_vectors::RecursiveArrayTools.ArrayPartition{T′, NTuple{N, Array{StaticArraysCore.SVector{D, T}, 1}}} where {D, T, N, T′}`: ノードの座標。
  * `group_sizes::NTuple{N, Int64} where N`: 不均一セル内の均一グループのサイズ。
  * `label::Union{Nothing, Symbol}`: セルのラベル。

`D`次元空間におけるノードの無秩序な不均一コレクション。この型は、セルのノードをいくつかのグループに分割することを可能にします。異なるノードのグループは、これらのノードを占有する物理オブジェクトの異なるクラスに対応する場合があります。
