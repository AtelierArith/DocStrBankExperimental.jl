```
(R_m, cp_m, cv_m, γ_m) = gas_constants(ts::ThermodynamicState)
```

熱力学状態 `ts` を与えると、すべての気体定数を一度に計算するラッパー。

関数は次のタプルを返します。

  * `R_m` [`gas_constant_air`](@ref)
  * `cp_m` [`cp_m`](@ref)
  * `cv_m` [`cv_m`](@ref)
  * `γ_m = cp_m/cv_m`
