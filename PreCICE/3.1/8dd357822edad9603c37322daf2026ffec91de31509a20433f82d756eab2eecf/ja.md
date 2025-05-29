```
setMeshVertices(meshName::String, positions::AbstractArray{Float64})::AbstractArray{Int32,1}
```

カップリングメッシュ上に複数のメッシュ頂点を作成し、それらのIDを保持する配列を返します。

# 引数

  * `meshName::String`: 頂点を追加するメッシュの名前。
  * `positions::AbstractArray{Float64}`: 頂点の座標を保持する配列。                                      形状は [N x D] で、N = 頂点の数、D = 幾何学の次元です。

# 注意事項

以前の呼び出し:

  * [`initialize`](@ref) はまだ呼び出されていません。

# 参照

[`getDimensions`](@ref), [`setMeshVertex`](@ref)

# 例

5つの頂点を持つ3D問題の例

```julia
vertices = [1 1 1;2 2 2;3 3 3]
vertex_ids = setMeshVertices("MeshOne", vertices)
```
