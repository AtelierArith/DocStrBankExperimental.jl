```
SBitstream(value::Real)
SBitstream{T<:Real}(value)
```

[-1, 1]の間の実数（浮動小数点数）を表す確率的ビットストリームです。

フィールド:

  * `bits::Vector{SBit}`: 基本となるビットストリーム
  * `value::Float64`: 表されている基本の浮動小数点数
