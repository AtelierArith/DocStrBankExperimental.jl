```
log_likelihood(gmm::GaussianMixtureModel, data::Matrix{<:Real})
```

ガウス混合モデル (GMM) に基づいてデータの対数尤度を計算します。データ行列は形状が (# 観測, # 特徴) である必要があります。

# 戻り値

  * `Float64`: モデルに基づくデータの対数尤度。
