```
normals(mesh::Mesh)
```

メッシュの法線を取得します。

# 引数

  * `mesh`: 法線を取得するメッシュ。

# 戻り値

メッシュの法線を含むベクトル。

# 例

```jldoctest; output=false
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> normals(m);
```
