```
eval_shapley(m::Chain, x, features::Vector{Symbol},
             N::Int      = min(10000,size(x,1)),
             num_mc::Int = 10)
```

グローバル特徴重要性のための確率的シャプレー効果を計算します。

参考: https://nredell.github.io/ShapML.jl/dev/#Examples-1

**引数:**

  * `m`:        ニューラルネットワークモデル
  * `x`:        `N` x `Nf` データ行列（`Nf` は特徴の数）
  * `features`: 長さ-`Nf` 特徴ベクトル（TL `A` の成分などを含む）
  * `N`:        （オプション）説明に使用するサンプル（インスタンス）の数
  * `num_mc`:   （オプション）モンテカルロシミュレーションの数

**戻り値:**

  * `df_shap`:       シャプレー効果のデータフレーム
  * `baseline_shap`: シャプレー効果の切片
