```
SinExp(l0, l1, period, decay)
SinExp(; l0, l1, period, decay)
```

`period` と指数的に減衰する振幅を持つ正弦波スケジュール。出力は次の式に従います。

```text
abs(l0 - l1) * Sin(t) * γ^(t - 1) + min(l0, l1)
```

ここで `Sin(t)` は `abs(sin(π * (t - 1) / period))` です（[`Sin`](@ref)を参照）。

# 引数

  * `range == abs(l0 - l1)`: 動的範囲（端点によって与えられる）
  * `offset == min(l0, l1)`: オフセット / 最小値
  * `period::Integer`: 周期
  * `decay`: 減衰率
