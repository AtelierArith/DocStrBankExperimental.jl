```
Center()
```

テーブルのすべての列にセンタートランスフォームを適用します。列 `x` のセンタートランスフォームは、平均 `μ` によって `x .- μ` と定義されます。

```
Center(col₁, col₂, ..., colₙ)
Center([col₁, col₂, ..., colₙ])
Center((col₁, col₂, ..., colₙ))
```

列 `col₁`, `col₂`, ..., `colₙ` にセンタートランスフォームを適用します。

```
Center(regex)
```

`regex` に一致する列にセンタートランスフォームを適用します。

# 例

```julia
Center(1, 3, 5)
Center([:a, :c, :e])
Center(("a", "c", "e"))
Center(r"[ace]")
```
