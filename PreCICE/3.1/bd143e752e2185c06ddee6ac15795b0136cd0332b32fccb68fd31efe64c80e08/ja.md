```
setMeshVertex(meshName::String, position::AbstractArray{Float64})::Integer
```

結合メッシュ上にメッシュ頂点を作成し、そのIDを返します。

# 引数

  * `meshName::String`: 頂点を追加するメッシュの名前。
  * `position::AbstractArray{Float64}`: 頂点の座標を持つ配列。次元に応じて、[x1, x2] または [x1,x2,x3] のいずれかです。

# 注意事項

以前の呼び出し:

  * 指定された位置の利用可能な要素の数は、設定された次元と一致します。

# 例

```julia
v1_id = setMeshVertex(mesh_name, [1,1,1])
```
