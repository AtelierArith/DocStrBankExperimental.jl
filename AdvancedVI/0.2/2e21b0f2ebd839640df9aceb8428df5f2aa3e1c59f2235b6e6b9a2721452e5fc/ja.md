```julia
struct ADVI{AD} <: AdvancedVI.VariationalInference{AD}
```

自動微分変分推論 (ADVI) 自動微分バックエンド `AD` を使用します。

# フィールド

  * `samples_per_step::Int64`: 各最適化ステップでELBOを推定するために使用されるサンプルの数。
  * `max_iters::Int64`: 最大勾配ステップ数。
  * `adtype::Any`: 自動微分に使用されるADバックエンド。
