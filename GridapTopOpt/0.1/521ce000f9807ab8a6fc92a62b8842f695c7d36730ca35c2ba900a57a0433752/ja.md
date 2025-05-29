```
struct AugmentedLagrangian <: Optimiser
```

NocedalとWrightによる2006年の拡張ラグランジュ法に基づいています（[link](https://doi.org/10.1007/978-0-387-40065-5)）。このメソッドは、`problem::PDEConstrainedFunctionals`に制約が定義されていない場合、ラグランジュ法として機能します。

# パラメータ

  * `problem::PDEConstrainedFunctionals`: 目的関数と制約の設定。
  * `ls_evolver::LevelSetEvolution`: 進化および再初期化方程式のソルバー。
  * `vel_ext::VelocityExtension`: 形状感度を計算領域に拡張するための速度拡張法。
  * `history::OptimiserHistory{Float64}`: 最適化問題の履歴情報。
  * `converged::Function`: 最適化者の収束をチェックするための関数。
  * `has_oscillations::Function`: 振動をチェックするための関数。
  * `params::NamedTuple`: 最適化パラメータ。

`has_oscillations`関数は、反復履歴における振動を避けるために追加されました。デフォルトでは、ChaosToolsに実装されている平均ゼロ交差アルゴリズムを使用します。振動チェックは、`has_oscillations = (args...) -> false`を取ることで無効にできます。
