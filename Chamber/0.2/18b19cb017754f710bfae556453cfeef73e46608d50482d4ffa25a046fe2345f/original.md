```
drho_dX_f(;eps_m::T, eps_g::T, eps_x::T, drho_m_dX::T, drho_g_dX::T, drho_x_dX::T, rho_x::T, rho_m::T, deps_x_dX::T)::T where {T<:Float64}
```

  * `X`: represent `P` or `T`
  * This function is used within the `build_rho_rc` function.

## Returns

  * `drho_dX`: represent `drho_dP` or `drho_dT`
