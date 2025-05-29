```
Triangle{T, S<:Integer}(l0, l1, period)
Triangle(; l0, l1, period)
```

`period`を持つ[三角波](https://en.wikipedia.org/wiki/Triangle_wave)スケジュール。出力は次の式に従います。

```text
abs(l0 - l1) * (2 / π) * abs(asin(sin(π * (t - 1) / period))) + min(l0, l1)
```

# 引数

  * `range == abs(l0 - l1)`: 動的範囲（端点によって与えられる）
  * `offset == min(l0, l1)`: オフセット / 最小値
  * `period::Integer`: 周期

```
