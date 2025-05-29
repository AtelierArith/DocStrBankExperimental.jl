```
eos(model::EoSModel, V, T, z=SA[1.0])
```

Returns the total Helmholtz free energy.

# Inputs:

  * `model::EoSModel` Thermodynamic model to evaluate
  * `V` Total volume, in [m³]
  * `T` Temperature, in [K]
  * `z` mole amounts, in [mol], by default is `@SVector [1.0]`

# Outputs:

  * Total Helmholtz free energy, in [J]

by default, it calls `R̄*T*∑(z)*(a_ideal(ideal_model,V,T,z) + a_res(model,V,T,z))` where `ideal_model == idealmodel(model)`, where `a_res` is the reduced residual Helmholtz energy and `a_ideal` is the reduced ideal Helmholtz energy. You can mix and match ideal models if you provide:

  * `[idealmodel](@ref)(model)`: extracts the ideal model from your Thermodynamic model
  * `[a_res](@ref)(model,V,T,z)`: residual reduced Helmholtz free energy
