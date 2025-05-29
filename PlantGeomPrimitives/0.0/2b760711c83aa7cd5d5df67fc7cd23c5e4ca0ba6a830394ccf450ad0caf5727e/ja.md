```
areas(m::Mesh)
```

メッシュを形成する異なる三角形の面積を持つベクトル。

# 引数

  * `mesh`: 面積を計算するメッシュ。

# 戻り値

メッシュを形成する異なる三角形の面積を持つベクトル。

# 例

```jldoctest
julia> r = Rectangle(length = 10.0, width = 0.2);

julia> areas(r);

julia> r = Rectangle(length = 10f0, width = 0.2f0);

julia> areas(r);
```
