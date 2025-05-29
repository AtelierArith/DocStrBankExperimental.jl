```
Pressure(; max_abs = nothing, max_rel = 0.2, scale = si_unit(:bar), maximum = Inf, minimum = DEFAULT_MINIMUM_PRESSURE)
```

Pressure変数の定義。`max_abs`/`max_rel`はニュートン反復における許容される最大絶対/相対変化、`scale`は線形システムを正則化するために使用される「典型的な」値、`maximum`は可能な最大値、`minimum`は最小値です。
