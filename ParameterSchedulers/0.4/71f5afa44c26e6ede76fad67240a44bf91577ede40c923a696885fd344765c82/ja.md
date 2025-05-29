```
TriangleExp{T, S<:Integer}(l0, l1, period, decay)
TriangleExp(; l0, l1, period, decay)
```

[三角波](https://en.wikipedia.org/wiki/Triangle_wave) スケジュールは `period` と指数関数的に減衰する振幅を持ちます。出力は次の式に従います。

```text
abs(l0 - l1) * Triangle(t) * decay^(t - 1) + min(l0, l1)
```

ここで `Triangle(t)` は `(2 / π) * abs(asin(sin(π * (t - 1) / schedule.period)))` です（[`Triangle`](@ref)を参照）。

# 引数

  * `range == abs(l0 - l1)`: 動的範囲（端点によって与えられる）
  * `offset == min(l0, l1)`: オフセット / 最小値
  * `period::Integer`: 周期
  * `decay`: 減衰率
