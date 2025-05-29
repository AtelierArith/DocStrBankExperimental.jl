```
area(mesh::Mesh)
```

メッシュの総表面積（個々の三角形の面積の合計）。

# 引数

  * `mesh`: 面積を計算するメッシュ。

# 戻り値

メッシュの総表面積を数値として返します。

# 例

```jldoctest
julia> r = Rectangle(length = 10.0, width = 0.2);

julia> area(r);

julia> r = Rectangle(length = 10f0, width = 0.2f0);

julia> area(r);
```
