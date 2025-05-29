```
TriangleDecay2{T, S<:Integer}(l0, l1, period)
TriangleDecay2(; l0, l1, period)
```

`period` と各サイクルの振幅の半分を持つ [三角波](https://en.wikipedia.org/wiki/Triangle_wave) スケジュール。出力は次の式に従います。

```text
abs(l0 - l1) * Triangle(t) / (2^floor((t - 1) / period)) + min(l0, l1)
```

ここで `Triangle(t)` は `(2 / π) * abs(asin(sin(π * (t - 1) / schedule.period)))` です（[`Triangle`](@ref) を参照）。

# 引数

  * `range == abs(l0 - l1)`: 動的範囲（端点によって与えられる）
  * `offset == min(l0, l1)`: オフセット / 最小値
  * `period::Integer`: 周期
