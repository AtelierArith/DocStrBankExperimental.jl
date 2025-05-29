```
build_co2(Pw::T, Pc::T, Temp::T, dPwdP::T, dPcdP::T, dPwdXco2::T, dPcdXco2::T)::NamedTuple{(:C_co2, :dC_co2dT, :dC_co2dP, :dC_co2dXco2),NTuple{4,T}} where {T<:Float64}
```

  * この関数は `exsolve` 関数内で使用されます。

## 戻り値

次のフィールドを持つ NamedTuple:

  * `C_co2`
  * `dC_co2dT`
  * `dC_co2dP`
  * `dC_co2dXco2`
