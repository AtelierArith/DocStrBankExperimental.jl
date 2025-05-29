```
build_meq(composition::Silicic, Pw::T, Pc::T, Temp::T, dPwdP::T, dPcdP::T, dPwdXco2::T, dPcdXco2::T)::NamedTuple{(:meq, :dmeqdT, :dmeqdP, :dmeqdXco2),NTuple{4,T}} where {T<:Float64}
```

  * This function is used within the `exsolve` function.

## Returns

A NamedTuple with the following fields:

  * `meq`
  * `dmeqdT`
  * `dmeqdP`
  * `dmeqdXco2`
