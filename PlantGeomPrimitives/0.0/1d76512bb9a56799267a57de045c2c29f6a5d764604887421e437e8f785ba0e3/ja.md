```
vertices(mesh::Mesh)
```

メッシュの頂点を取得します。

# 引数

  * `mesh`: 頂点を取得するメッシュ。

# 戻り値

メッシュの頂点を含むベクトル。

# 例

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> vertices(m);
```
