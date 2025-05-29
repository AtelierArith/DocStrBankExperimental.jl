```
build_meq(composition::Mafic, P::T, Temp::T, X_co2::T)::NamedTuple{(:meq, :dmeqdT, :dmeqdP, :dmeqdXco2),NTuple{4,T}} where {T<:Float64}
```

  * この関数は `exsolve` 関数内で使用されます。

## 戻り値

以下のフィールドを持つ NamedTuple:

  * `meq`
  * `dmeqdT`
  * `dmeqdP`
  * `dmeqdXco2`
