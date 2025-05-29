```
A = CartesianMeshArray(inds...; step, origin=nothing)
```

は、形状 `inds...` と指定された `step` および `origin` を持つ `N` 次元の直交メッシュを表す抽象配列 `A` を構築します。構文 `A[i1,i2,...]` は、インデックス `(i1,i2,...)` のノードの座標を返します。ノードインデックスは、`Int` のタプルまたは `CartesianIndex` として指定することもできます。座標は遅延計算され、ストレージは `O(1)` です。

引数 `step` と `origin` の説明については、[`CartesianMesh`](@ref StructuredArrays.Meshes.CartesianMesh) も参照してください。
