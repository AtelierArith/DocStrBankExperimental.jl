```
water(composition::Silicic, p::T, t::T, x::T, c::T)::T where {T<:Float64}
```

  * 水の分配関数
  * この関数は `exsolve3` 関数内で使用されます。

## 引数

  * `p`: 圧力 (Pa)
  * `t`: 温度 (K)
  * `x`: 前のCO2モル分率 (X_CO2)
  * `c`: 水の量
