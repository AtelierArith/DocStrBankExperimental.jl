```
DropExtrema(; low=0.25, high=0.75)
```

すべての列の値が区間（`[quantile(col, low), quantile(col, high)]`）の外にある行を削除します。

```
DropExtrema(col₁, col₂, ..., colₙ; low=0.25, high=0.75)
DropExtrema([col₁, col₂, ..., colₙ]; low=0.25, high=0.75)
DropExtrema((col₁, col₂, ..., colₙ); low=0.25, high=0.75)
```

列 `col₁`, `col₂`, ..., `colₙ` の値が区間の外にある行を削除します。

```
DropExtrema(regex; low=0.25, high=0.75)
```

`regex` に一致する列の値が区間の外にある行を削除します。

# 例

```julia
DropExtrema(low=0.3, high=0.7)
DropExtrema(1, low=0.3, high=0.7)
DropExtrema(:a, low=0.2, high=0.8)
DropExtrema("a", low=0.3, high=0.7)
DropExtrema(1, 3, 5, low=0, high=1)
DropExtrema([:a, :c, :e], low=0.3, high=0.7)
DropExtrema(("a", "c", "e"), low=0.25, high=0.75)
DropExtrema(r"[ace]", low=0.3, high=0.7)
```
