```
LowHigh(; low=0.25, high=0.75)
```

テーブルのすべての列にLowHigh変換を適用します。列`x`のLowHigh変換は、`(x .- xl) ./ (xh - xl)`で定義され、ここで`xl = quantile(x, low)`および`xh = quantile(x, high)`です。

```
LowHigh(col₁, col₂, ..., colₙ; low=0.25, high=0.75)
LowHigh([col₁, col₂, ..., colₙ]; low=0.25, high=0.75)
LowHigh((col₁, col₂, ..., colₙ); low=0.25, high=0.75)
```

列`col₁`、`col₂`、...、`colₙ`にLowHigh変換を適用します。

```
LowHigh(regex; low=0.25, high=0.75)
```

`regex`に一致する列にLowHigh変換を適用します。

# 例

```julia
LowHigh()
LowHigh(low=0, high=1)
LowHigh(low=0.3, high=0.7)
LowHigh(1, 3, 5, low=0, high=1)
LowHigh([:a, :c, :e], low=0.3, high=0.7)
LowHigh(("a", "c", "e"), low=0.25, high=0.75)
LowHigh(r"[ace]", low=0.3, high=0.7)
```
