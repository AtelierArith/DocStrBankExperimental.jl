```julia
struct JitterTune{B<:BaytesCore.UpdateBool}
```

ジッタリングを適用する必要があるかどうかを決定するコンテナ

# フィールド

  * `adaption::BaytesCore.UpdateBool`: 適応型ジッタリングが適用されているかどうかのブール値。falseの場合、常に最大ステップがジッタリングされる。
  * `Nsteps::BaytesCore.Iterator`: ジッタリング中に実行されるジッタリングステップの数。
  * `threshold::Float64`: パラメータの相関に対するジッタリング閾値。
  * `min::Int64`: ジッタリングステップの最小数。
  * `max::Int64`: ジッタリングステップの最大数。
