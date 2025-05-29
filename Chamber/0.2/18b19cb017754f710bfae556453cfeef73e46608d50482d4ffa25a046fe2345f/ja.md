```
drho_dX_f(;eps_m::T, eps_g::T, eps_x::T, drho_m_dX::T, drho_g_dX::T, drho_x_dX::T, rho_x::T, rho_m::T, deps_x_dX::T)::T where {T<:Float64}
```

  * `X`: は `P` または `T` を表します
  * この関数は `build_rho_rc` 関数内で使用されます。

## 戻り値

  * `drho_dX`: は `drho_dP` または `drho_dT` を表します
