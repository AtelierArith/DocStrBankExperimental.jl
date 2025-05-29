```
build_rho_rc(eps_m::T, eps_g::T, eps_x::T, rho_m::T, rho_g::T, rho_x::T, drho_m_dP::T, drho_g_dP::T, drho_x_dP::T, drho_m_dT::T, drho_g_dT::T, drho_x_dT::T, c_x::T, c_m::T, c_g::T, deps_x_dP::T, deps_x_dT::T)::Vector{T} where {T<:Float64}
```

  * This function is used within the `odeChamber` function.

## Returns

[`rho`, `drho_dP`, `drho_dT`, `drho_deps_g`, `rc`, `drc_dP`, `drc_dT`]
