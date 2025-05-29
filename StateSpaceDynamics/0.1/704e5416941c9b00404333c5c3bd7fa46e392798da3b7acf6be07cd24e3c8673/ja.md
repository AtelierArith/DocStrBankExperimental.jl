```
fit!(pmm::PoissonMixtureModel, data::Matrix{Int}; <keyword arguments>)
```

ポアソン混合モデル（PMM）を与えられたデータに対して期待値最大化（EM）アルゴリズムを使用してフィットさせます。

# 引数

  * `pmm::PoissonMixtureModel`: フィットさせるポアソン混合モデル。
  * `data::Matrix{Int}`: モデルがフィットされるデータセットで、各行はデータポイントを表します。
  * `maxiter::Int=50`: EMアルゴリズムの最大反復回数（デフォルト: 50）。
  * `tol::Float64=1e-3`: 収束のための許容誤差。反復間の対数尤度の変化がこの値未満になるとアルゴリズムは停止します（デフォルト: 1e-3）。
  * `initialize_kmeans::Bool=false`: trueの場合、K-means++初期化を使用してPMMの平均を初期化します（デフォルト: false）。

# 戻り値

  * `class_probabilities`: 各エントリ (i, k) がi番目のデータポイントが混合モデルのk番目の成分に属する確率を表す行列。

# 例

```julia
data = rand(1:10, 100, 1)  # ランダムな整数データを生成
pmm = PoissonMixtureModel(k=3)  # 3つの成分を持つPMMを初期化
class_probabilities = fit!(pmm, data, maxiter=100, tol=1e-4, initialize_kmeans=true)
```
