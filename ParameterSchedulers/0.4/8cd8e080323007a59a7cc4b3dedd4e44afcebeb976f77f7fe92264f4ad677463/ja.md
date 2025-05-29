```
SinDecay2(l0, l1, period)
SinDecay2(; l0, l1, period)
```

周期と各サイクルの振幅の半分を持つ正弦波スケジュール。出力は次の式に従います。

```text
abs(l0 - l1) * Sin(t) / (2^floor((t - 1) / period)) + min(l0, l1)
```

ここで、`Sin(t)`は`abs(sin(π * (t - 1) / period))`です（[`Sin`](@ref）を参照）。

# 引数

  * `range == abs(l0 - l1)`: 動的範囲（端点によって与えられる）
  * `offset == min(l0, l1)`: オフセット / 最小値
  * `period::Integer`: 周期
