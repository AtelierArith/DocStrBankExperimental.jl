```
coherentthermalstate(v::VibrationalMode, n̄::Real, α::Number; method="truncated)
```

`v`に対して、熱状態に変位操作を適用することによって生成される変位熱状態を返します。熱状態の平均占有数は`n̄`であり、`α`は変位の複素振幅です。

`method`は`"truncated"`または`"analytic"`のいずれかであり、この引数は変位演算子がどのように計算されるかを決定します（参照: [`displace`](@ref)）。
