```
IpoptOptions(; kwargs...)
```

`IpoptOptimizer`を使用したパラメータ推定のオプション。

オプションの詳細については、Ipoptの[ドキュメント](https://coin-or.github.io/Ipopt/)を参照してください。

また、[`IpoptOptimizer`](@ref)、[`calibrate`](@ref)、および[`calibrate_multistart`](@ref)も参照してください。

## キーワード引数

  * `print_level = 0`: 出力の冗長性レベル（有効な値は 0 ≤ print_level ≤ 12）
  * `max_iter = 1000`: 最大反復回数
  * `tol = 1e-8`: 相対収束許容誤差
  * `acceptable_tol = 1e-6`: 受け入れ可能な相対収束許容誤差
  * `max_wall_time 1e20`: 最長壁時間、最適化が実行されることが許可されている時間
  * `acceptable_obj_change_tol 1e20`: 目的関数の変化に基づく受け入れ停止基準。
