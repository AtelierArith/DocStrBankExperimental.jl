```
SimpleTrustRegion(;
    autodiff = AutoForwardDiff(), max_trust_radius = 0.0,
    initial_trust_radius = 0.0, step_threshold = nothing,
    shrink_threshold = nothing, expand_threshold = nothing,
    shrink_factor = 0.25, expand_factor = 2.0, max_shrink_times::Int = 32,
    nlsolve_update_rule = Val(false)
)
```

トラストリージョンソルバーの低オーバーヘッド実装。このメソッドは、スカラーおよび静的配列の問題に対してメモリを割り当てません。

### キーワード引数

  * `autodiff`: ヤコビアンに使用されるバックエンドを決定します。デフォルトは `nothing`（すなわち自動バックエンド選択）です。有効な選択肢には `DifferentiationInterface.jl` のヤコビアンバックエンドが含まれます。
  * `max_trust_radius`: トラストリージョンの最大半径です。デフォルトは `max(norm(f(u0)), maximum(u0) - minimum(u0))` です。
  * `initial_trust_radius`: 初期トラストリージョン半径です。デフォルトは `max_trust_radius / 11` です。
  * `step_threshold`: ステップを取るための閾値です。各イテレーションで、閾値は値 `r` と比較されます。`r` は目的関数の実際の減少を予測された減少で割ったものです。`step_threshold > r` の場合、モデルは良い近似ではなく、ステップは拒否されます。デフォルトは `0.0001` です。詳細については、[Rahpeymaii, F.](https://link.springer.com/article/10.1007/s40096-020-00339-4) を参照してください。
  * `shrink_threshold`: トラストリージョン半径を縮小するための閾値です。各イテレーションで、閾値は値 `r` と比較されます。`r` は目的関数の実際の減少を予測された減少で割ったものです。`shrink_threshold > r` の場合、トラストリージョン半径は `shrink_factor` によって縮小されます。デフォルトは `0.25` です。詳細については、[Rahpeymaii, F.](https://link.springer.com/article/10.1007/s40096-020-00339-4) を参照してください。
  * `expand_threshold`: トラストリージョン半径を拡大するための閾値です。ステップが取られた場合、すなわち `step_threshold < r`（`r` は `shrink_threshold` で定義される）で、`expand_threshold < r` かどうかもチェックされます。それが真であれば、トラストリージョン半径は `expand_factor` によって拡大されます。デフォルトは `0.75` です。
  * `shrink_factor`: `shrink_threshold > r` の場合（`r` は `shrink_threshold` で定義される）、トラストリージョン半径を縮小するための係数です。デフォルトは `0.25` です。
  * `expand_factor`: `expand_threshold < r` の場合（`r` は `shrink_threshold` で定義される）、トラストリージョン半径を拡大するための係数です。デフォルトは `2.0` です。
  * `max_shrink_times`: トラストリージョン半径を連続して縮小する最大回数です。`max_shrink_times` を超えると、アルゴリズムは終了します。デフォルトは `32` です。
  * `nlsolve_update_rule`: `Val(true)` に設定すると、NLSolve.jl の更新ルールを使用してトラストリージョン半径を更新します。デフォルトは `Val(false)` です。`Val(true)` に設定すると、いくつかの半径更新パラメータ – `step_threshold = 0.05`、`expand_threshold = 0.9`、および `shrink_factor = 0.5` – のデフォルトが異なります。
