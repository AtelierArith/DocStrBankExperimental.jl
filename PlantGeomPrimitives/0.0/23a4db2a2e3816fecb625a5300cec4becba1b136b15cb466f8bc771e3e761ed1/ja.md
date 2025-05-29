```
ntriangles(mesh)
```

メッシュ内の三角形の数を抽出します。

# 引数

  * `mesh`: 三角形の数を抽出するメッシュ。

# 戻り値

メッシュ内の三角形の数を整数として返します。

# 例

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> ntriangles(m);
```
