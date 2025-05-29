```
Coalesce(; value)
```

テーブルのすべての `missing` 値を `value` で置き換えます。

```
Coalesce(col₁, col₂, ..., colₙ; value)
Coalesce([col₁, col₂, ..., colₙ]; value)
Coalesce((col₁, col₂, ..., colₙ); value)
```

列 `col₁`, `col₂`, ..., `colₙ` のすべての欠損値を `value` で置き換えます。

```
Coalesce(regex; value)
```

`regex` に一致する列のすべての欠損値を `value` で置き換えます。

# 例

```julia
Coalesce(value=0)
Coalesce(1, 3, 5, value=1)
Coalesce([:a, :c, :e], value=2)
Coalesce(("a", "c", "e"), value=3)
Coalesce(r"[ace]", value=4)
```

## 注意事項

  * この変換は、列の要素型を `Union{Missing,T}` から `T` に変更することがあります。
