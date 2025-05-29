```
modelX_gaussian_rep_group_knockoffs(X, method, groups; [m], [covariance_approximator], [kwargs...])
modelX_gaussian_rep_group_knockoffs(X, method, groups, μ, Σ; [m], [kwargs...])
```

各グループから代表を選択し、代表のみに基づいて小さな最適化問題を解くことによってグループノックオフを構築します。残りのノックオフは、グラフィカルモデルに似た条件付き独立性の仮定に基づいて生成されます（詳細は後で説明します）。代表は[`choose_group_reps`](@ref)によって計算されます。

# 入力

  * `X`: `n × p` デザイン行列。各行はサンプル、各列は特徴です。
  * `method`: ノックオフを構築するためのメソッド。オプションは `modelX_gaussian_group_knockoffs` と同じです。
  * `groups`: グループメンバーシップを示す `Int` のベクター。`groups[i]` は `X[:, i]` のグループです。
  * `covariance_approximator`: 共分散推定器で、デフォルトは `LinearShrinkage(DiagonalUnequalVariance(), :lw)` です。詳細は CovarianceEstimation.jl を参照してください。
  * `μ`: `X` の真の列平均を格納する長さ `p` のベクター。
  * `Σ`: `X` の列のための `p × p` 共分散行列。
  * `rep_threshold`: 各グループの代表者の数を制御する0と1の間の値。大きいほど多くの代表者を意味します（デフォルトは0.5）。
  * `m`: 変数ごとのノックオフの数で、デフォルトは1です。
  * `kwargs`: `solve_s_group` のための追加のキーワード引数。
