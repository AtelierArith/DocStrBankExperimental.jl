```
(R_m, cp_m, cv_m, γ_m) = gas_constants(param_set, q::PhasePartition)
```

すべてのガス定数を一度に計算するためのラッパーで、オプションとして、

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `q` は [`PhasePartition`](@ref) です。

この関数は次のタプルを返します。

  * `R_m` は [`gas_constant_air`](@ref)
  * `cp_m` は [`cp_m`](@ref)
  * `cv_m` は [`cv_m`](@ref)
  * `γ_m = cp_m/cv_m`
