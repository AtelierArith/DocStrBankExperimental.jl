```
(R_m, cp_m, cv_m, γ_m) = gas_constants([q::PhasePartition])
```

すべてのガス定数を一度に計算するラッパーで、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気のものになります。

関数は次のタプルを返します。

  * `R_m` [`gas_constant_air`](@ref)
  * `cp_m` [`cp_m`](@ref)
  * `cv_m` [`cv_m`](@ref)
  * `γ_m = cp_m/cv_m`
