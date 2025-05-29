```
get_eps_g(composition::Union{Silicic,Mafic}, eps_g_prev::Float64, X_co20::Float64, P::Float64, T::Float64, eps_x0::Float64, V::Float64, rho_m::Float64, rho_g::Float64, M_h2o::Float64, M_co2::Float64)::NamedTuple{(:eps_g0, :mco2_diss),NTuple{2,Float64}}
```

  * This function is used within the `IC_Finder` function to get eps*g0 and mco2*diss.

## Returns

A NamedTuple with the following fields:

  * `eps_g0`
  * `mco2_diss`
