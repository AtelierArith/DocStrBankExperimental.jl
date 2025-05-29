```
struct HilbertianProjection <: Optimiser
```

Wegert et al. (2023) によって説明されたヒルベルト射影法 ([link](https://doi.org/10.1007/s00158-023-03663-0))。

# パラメータ

  * `problem::PDEConstrainedFunctionals{N}`: 目的関数と制約の設定。
  * `ls_evolver::LevelSetEvolution`: 進化と再初期化方程式のソルバー。
  * `vel_ext::VelocityExtension`: 形状感度を計算領域に拡張するための速度拡張法。
  * `projector::HilbertianProjectionMap`: 感度情報の投影器。
  * `history::OptimiserHistory{Float64}`: 最適化問題のための履歴情報。
  * `converged::Function`: 最適化者の収束をチェックするための関数。
  * `has_oscillations::Function`: 振動をチェックするための関数。
  * `params::NamedTuple`: 最適化パラメータ。
