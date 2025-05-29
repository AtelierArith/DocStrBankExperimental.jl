```
padic_field(p::Integer; precision::Int=64, cached::Bool=true, check::Bool=true)
padic_field(p::ZZRingElem; precision::Int=64, cached::Bool=true, check::Bool=true)
```

与えられた素数 $p$ に対する $p$-進体を返します。体の要素のデフォルトの絶対精度は `precision` で設定できます。
