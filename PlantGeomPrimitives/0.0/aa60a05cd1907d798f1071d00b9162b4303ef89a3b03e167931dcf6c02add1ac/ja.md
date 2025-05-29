```
nvertices(mesh)
```

メッシュ内の頂点の数。

# 引数

  * `mesh`: 頂点の数を取得するメッシュ。

# 戻り値

メッシュ内の頂点の数を整数として返します。

# 例

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> nvertices(m);
```
