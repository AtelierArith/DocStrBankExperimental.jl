```
create_random_bounded_ews(
    d,
    standardBasis::StandardBasis,
    n,
    sphericalOnly::Bool,
    iterations::Integer,
    method=Optim.NelderMead,
    useConstrainedOpt=false
)
```

`n` 個の `BoundedEW` の配列を返します。$d^2$ の `standardBasis` 座標は、`sphericalOnly` が false の場合は [-1, 1] の範囲で一様に分布し、そうでない場合は単位球上で一様に分布します。

`iterations` 回の実行を使用して、Optim.jl の最適化手法 `method` で最適化を改善します。
