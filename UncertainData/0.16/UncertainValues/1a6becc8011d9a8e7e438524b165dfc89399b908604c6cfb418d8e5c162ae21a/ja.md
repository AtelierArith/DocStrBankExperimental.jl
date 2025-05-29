```
struct ConstrainedUncertainScalarValueOneParameter{S, T1 <: Number}
    distribution::Distribution{Univariate, S}
    a::T1
end
```

一つのパラメータ分布によって表される制約付き不確実値であり、元の分布が切り取られています。

## フィールド:

  * **`distribution`**: 元の分布の切り取られたバージョン。
  * **`a`**: 元の分布のパラメータの元の値。
