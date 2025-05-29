```
build_co2(Pw::T, Pc::T, Temp::T, dPwdP::T, dPcdP::T, dPwdXco2::T, dPcdXco2::T)::NamedTuple{(:C_co2, :dC_co2dT, :dC_co2dP, :dC_co2dXco2),NTuple{4,T}} where {T<:Float64}
```

  * This function is used within the `exsolve` function.

## Returns

A NamedTuple with the following fields:

  * `C_co2`
  * `dC_co2dT`
  * `dC_co2dP`
  * `dC_co2dXco2`
