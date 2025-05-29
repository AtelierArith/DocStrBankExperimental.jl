```
dwater_dx(composition::Mafic, p::T, t::T, x::T)::T where {T<:Float64}
```

  * 水の分配関数のX_CO2に関する導関数
  * この関数は`exsolve3`関数内で使用されます。

## 引数

  * `p`: 圧力 (Pa)
  * `t`: 温度 (K)
  * `x`: 前のCO2のモル分率 (X_CO2)
