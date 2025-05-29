```
struct ConstrainedUncertainScalarValueTwoParameter{S, T1 <: Number, T2 <: Number}
    distribution::Distribution{Univariate, S}
    a::T1
    b::T2
end
```

2つのパラメータを持つ分布によって表される制約付き不確実値であり、元の分布が切り詰められています。

## フィールド:

  * **`distribution`**: 元の分布の切り詰められたバージョン。
  * **`a`**: 元の分布の最初のパラメータの元の値。
  * **`b`**: 元の分布の2番目のパラメータの元の値。
