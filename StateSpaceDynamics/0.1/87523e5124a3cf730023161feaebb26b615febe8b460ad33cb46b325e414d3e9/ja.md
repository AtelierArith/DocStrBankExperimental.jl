```
ポアソン混合モデル
```

クラスタリングと密度推定のためのポアソン混合モデル。

## フィールド

  * `k::Int`: ポアソン分布に従うクラスタの数。
  * `λₖ::Vector{Float64}`: 各クラスタの平均。
  * `πₖ::Vector{Float64}`: 各クラスタの混合係数。

## 例

`julia pmm = PoissonMixtureModel(3) # 3つのクラスタ、2次元データ fit!(pmm, data)`
