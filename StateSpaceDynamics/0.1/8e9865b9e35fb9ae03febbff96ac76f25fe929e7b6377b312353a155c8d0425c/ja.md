```
fit!(gmm::GaussianMixtureModel, data::Matrix{<:Real}; <keyword arguments>)
```

与えられたデータに対して期待値最大化（EM）アルゴリズムを使用してガウス混合モデル（GMM）を適合させます。

# 引数

  * `gmm::GaussianMixtureModel`: 適合させるガウス混合モデル。
  * `data::Matrix{<:Real}`: モデルが適合されるデータセットで、各行はデータポイントを表します。
  * `maxiter::Int=50`: EMアルゴリズムの最大反復回数（デフォルト: 50）。
  * `tol::Float64=1e-3`: 収束のための許容誤差。反復間の対数尤度の変化がこの値未満になるとアルゴリズムは停止します（デフォルト: 1e-3）。
  * `initialize_kmeans::Bool=false`: trueの場合、K-means++初期化を使用してGMMの平均を初期化します（デフォルト: false）。

# 戻り値

  * `class_probabilities`: 各エントリ (i, k) がi番目のデータポイントが混合モデルのk番目の成分に属する確率を表す行列。

# 例

```julia
data = rand(2, 100)  # ランダムデータを生成
gmm = GaussianMixtureModel(k=3, d=2)  # 3つの成分と2次元データを持つGMMを初期化
class_probabilities = fit!(gmm, data, maxiter=100, tol=1e-4, initialize_kmeans=true)
```
