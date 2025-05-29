```
Quantile(; dist=Normal())
```

指定された `distribution` に対する分位数変換。

```
Quantile(col₁, col₂, ..., colₙ; dist=Normal())
Quantile([col₁, col₂, ..., colₙ]; dist=Normal())
Quantile((col₁, col₂, ..., colₙ); dist=Normal())
```

列 `col₁`, `col₂`, ..., `colₙ` に分位数変換を適用します。

```
Quantile(regex; dist=Normal())
```

`regex` に一致する列に分位数変換を適用します。

# 例

```julia
using Distributions

Quantile()
Quantile(dist=Normal())
Quantile(1, 3, 5, dist=Beta())
Quantile([:a, :c, :e], dist=Gamma())
Quantile(("a", "c", "e"), dist=Beta())
Quantile(r"[ace]", dist=Normal())
```
