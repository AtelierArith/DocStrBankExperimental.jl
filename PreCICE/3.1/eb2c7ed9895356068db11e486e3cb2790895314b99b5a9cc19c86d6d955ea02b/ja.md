```
setMeshEdges(meshName::String, vertices::AbstractArray{Cint})
```

複数のメッシュエッジを作成する

# 引数

  * `meshName::String`: エッジを追加するメッシュの名前。
  * `vertices::AbstractArray{Cint}`: エッジの頂点IDを保持する配列。                                  形状は [N x 2] で、N はエッジの数です。

# 例

4つのメッシュ頂点を持つ問題のために、両対角線が完全に相互接続された正方形の形でメッシュエッジを設定します。

```julia-repl
julia> vertices = [1 2; 1 3; 1 4; 2 3; 2 4; 3 4]
julia> vertices.shape
(6,2)
julia> setMeshEdges("MeshOne", vertices)
```
