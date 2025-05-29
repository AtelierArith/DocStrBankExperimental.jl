```
tf = TransferFunction([1, 2], [3, 5, 8])
tf = TransferFunction([1, 2], [3, 5, 8], 3.0)
```

線形時間不変システムを表す伝達関数を構築します。

# 例

伝達関数を構築するには

$$
G(s) = \frac{4e^{-2.2s}}{2s+1}
$$

Juliaでは：

```jldoctest
tf = TransferFunction([4], [2, 1], 2.2)
# 出力
    4.0
----------- e^(-2.2*s)
2.0*s + 1.0
```

# 属性

  * `numerator::Polynomial{Float64, :s}`: 伝達関数の分子の多項式
  * `denominator::Polynomial{Float64, :s}`: 伝達関数の分母の多項式
  * `time_delay::Float64`: 関連する時間遅延
