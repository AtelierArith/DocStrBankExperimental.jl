```
build_meq(composition::Silicic, Pw::T, Pc::T, Temp::T, dPwdP::T, dPcdP::T, dPwdXco2::T, dPcdXco2::T)::NamedTuple{(:meq, :dmeqdT, :dmeqdP, :dmeqdXco2),NTuple{4,T}} where {T<:Float64}
```

  * この関数は `exsolve` 関数内で使用されます。

## 戻り値

以下のフィールドを持つ NamedTuple:

  * `meq`
  * `dmeqdT`
  * `dmeqdP`
  * `dmeqdXco2`
