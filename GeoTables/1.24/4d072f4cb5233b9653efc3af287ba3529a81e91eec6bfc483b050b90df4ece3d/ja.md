```
@groupby(geotable, col₁, col₂, ..., colₙ)
@groupby(geotable, [col₁, col₂, ..., colₙ])
@groupby(geotable, (col₁, col₂, ..., colₙ))
```

ジオスペーシャル `geotable` を列 `col₁`, `col₂`, ..., `colₙ` でグループ化します。

```
@groupby(geotable, regex)
```

ジオスペーシャル `geotable` を `regex` に一致する列でグループ化します。

# 例

```julia
@groupby(geotable, 1, 3, 5)
@groupby(geotable, [:a, :c, :e])
@groupby(geotable, ("a", "c", "e"))
@groupby(geotable, r"[ace]")
```
