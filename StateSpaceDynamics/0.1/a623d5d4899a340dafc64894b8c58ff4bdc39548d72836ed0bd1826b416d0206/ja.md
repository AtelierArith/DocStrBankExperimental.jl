```
log_likelihood(pmm::PoissonMixtureModel, data::Matrix{Int})
```

ポアソン混合モデル（PMM）に基づいてデータの対数尤度を計算します。データ行列は形状が（# 観測、# 特徴）である必要があります。

# 戻り値

  * `Float64`: モデルに基づくデータの対数尤度。
