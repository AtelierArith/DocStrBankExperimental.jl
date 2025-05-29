```
drc_dX_f(;eps_x::T, c_x::T, drho_x_dX::T, eps_g::T, c_g::T, drho_g_dX::T, eps_m::T, c_m::T, drho_m_dX::T, rho_x::T, rho_m::T, deps_x_dX::T)::T where {T<:Float64}
```

Computing the derivatives of the product of density and specific heat for the mixture

  * `X`: represent `P` or `T`
  * This function is used within the `build_rho_rc` function.

## Returns

  * `drc_dX`: represent `drc_dP` or `drc_dT`
