```
build_meq(composition::Mafic, P::T, Temp::T, X_co2::T)::NamedTuple{(:meq, :dmeqdT, :dmeqdP, :dmeqdXco2),NTuple{4,T}} where {T<:Float64}
```

  * This function is used within the `exsolve` function.

## Returns

A NamedTuple with the following fields:

  * `meq`
  * `dmeqdT`
  * `dmeqdP`
  * `dmeqdXco2`
