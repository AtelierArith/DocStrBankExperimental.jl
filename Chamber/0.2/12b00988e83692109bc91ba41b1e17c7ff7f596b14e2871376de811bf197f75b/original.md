```
get_phase(composition::Union{Silicic,Mafic}, P::Float64, T::Float64, V::Float64, rho_m::Float64, M_h2o::Float64, M_co2::Float64, eps_x0::Float64)::NamedTuple{(:phase, :m_co2_melt),NTuple{2,Float64}}
```

  * This function is used within the `IC_Finder` function to determine the initial phase.

## Returns

A NamedTuple with the following fields:

  * `phase`: 2 or 3
  * `m_co2_melt`
