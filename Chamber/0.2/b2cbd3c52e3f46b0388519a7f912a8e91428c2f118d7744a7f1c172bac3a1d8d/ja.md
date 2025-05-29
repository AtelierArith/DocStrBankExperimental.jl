```
drc_dX_f(;eps_x::T, c_x::T, drho_x_dX::T, eps_g::T, c_g::T, drho_g_dX::T, eps_m::T, c_m::T, drho_m_dX::T, rho_x::T, rho_m::T, deps_x_dX::T)::T where {T<:Float64}
```

混合物の密度と比熱の積の導関数を計算する

  * `X`: `P` または `T` を表す
  * この関数は `build_rho_rc` 関数内で使用される。

## 戻り値

  * `drc_dX`: `drc_dP` または `drc_dT` を表す
