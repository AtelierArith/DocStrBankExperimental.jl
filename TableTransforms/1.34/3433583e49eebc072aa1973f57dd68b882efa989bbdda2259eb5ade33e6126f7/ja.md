```
MinMax()
```

テーブルのすべての列にMinMax変換を適用します。MinMax変換は`LowHigh(low=0, high=1)`と同等です。

```
MinMax(col₁, col₂, ..., colₙ)
MinMax([col₁, col₂, ..., colₙ])
MinMax((col₁, col₂, ..., colₙ))
```

列`col₁`、`col₂`、...、`colₙ`にMinMax変換を適用します。

```
MinMax(regex)
```

`regex`に一致する列にMinMax変換を適用します。

# 例

```julia
MinMax(1, 3, 5)
MinMax([:a, :c, :e])
MinMax(("a", "c", "e"))
MinMax(r"[ace]")
```

[`LowHigh`](@ref)も参照してください。
