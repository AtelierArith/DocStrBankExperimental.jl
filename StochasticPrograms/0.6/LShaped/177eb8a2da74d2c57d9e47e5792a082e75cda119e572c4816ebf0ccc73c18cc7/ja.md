```
CombinatorialCuts
```

[`CombinatorialCuts`](@ref) のファクトリーオブジェクト。`LShaped.Optimizer` の `integer_strategy` に渡すか、[`IntegerStrategy`](@ref) 属性を設定します。

...

# パラメータ

  * `lower_bound::AbstractFloat = -1e10`: 第二段階の目的に対する下限を設定し、近似する必要をなくします。
  * `alternate::Bool = false`: アルゴリズムが緩和された問題を解く（通常の最適性カットを生成）と緩和されていない問題を解く（組合せカットを生成）を交互に行うかどうかを指定します。
  * `update_L_every::Integer = 0`: 下限近似を更新する頻度を設定します。ゼロに設定した場合は一度だけ近似します。
  * `optimizer = nothing`: `LiftAndProject` または `CuttingPlaneTree` 戦略で補助問題を解くために使用されるオプティマイザをオプションで指定します。

...
