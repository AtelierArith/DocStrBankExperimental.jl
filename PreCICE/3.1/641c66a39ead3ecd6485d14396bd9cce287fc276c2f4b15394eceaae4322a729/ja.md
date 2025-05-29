```
setMeshTriangles(meshName::String, vertices::AbstractArray{Integer})
```

頂点IDからメッシュ三角形を設定します。

# 引数

  * `meshName::String`: エッジを追加するメッシュの名前。
  * `vertices::AbstractArray{Integer}`: 三角形の頂点のID。

# 例

対角線が完全に相互接続された正方形の形をした4つのメッシュ頂点を持つ問題のためにメッシュ三角形を設定します。

```julia-repl
julia> vertices = [1 2 3; 1 3 4; 1 2 4; 1 3 4]
julia> vertices.shape
(4,3)
julia> setMeshTriangles("MeshOne", vertices)
```
