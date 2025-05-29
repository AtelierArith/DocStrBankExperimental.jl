```
Mesh(vertices)
```

ベクトルの頂点から三角形メッシュを生成します。

# 引数

  * `vertices`: 頂点のリスト（各頂点は `Vec` として実装されています）。

# 戻り値

`Mesh` オブジェクト。

# 例

```jldoctest
julia> verts = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> Mesh(verts);
```
