```
struct ConstrainedUncertainScalarValueThreeParameter{S, T1 <: Number, T2 <: Number, T3 <: Number}
    distribution::Distribution{Univariate, S}
    a::T1
    b::T2
    c::T3
end
```

二つのパラメータの分布によって表される制約付き不確実値であり、元の分布が切り詰められています。

## フィールド:

  * **`distribution`**: 元の分布の切り詰められたバージョン。
  * **`a`**: 元の分布の最初のパラメータの元の値。
  * **`b`**: 元の分布の二番目のパラメータの元の値。
  * **`c`**: 元の分布の三番目のパラメータの元の値。
