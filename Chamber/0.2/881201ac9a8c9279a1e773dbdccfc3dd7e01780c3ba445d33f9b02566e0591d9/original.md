```
heat_conduction_chamber_profileCH(maxn::Int64, a::Float64, c::Float64, r::Float64, kappa::Float64, Tb::Float64, param_sv::ParamSaved{Float64})::Float64
```

Calculates the heat transfer in a magma chamber based on the thermal diffusivity of the host rocks and the temperature profile of the outer shell.

## Arguments

  * `maxn`: number of terms
  * `a`: radius of magma chamber (m)
  * `c`: radius of outer shell (m)
  * `r`: grid spacing of calculate the heat transfer
  * `kappa`: thermal diffusivity of host rocks
  * `Tb`: boundary temperature of the outer shell (K)
  * `param_sv`: a struct `ParamSaved` stores the previous results of the function

## Returns

  * `Trt`
