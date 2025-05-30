```julia
struct ConfigProposal{A<:BaytesCore.UpdateBool, M<:BaytesMCMC.MatrixMetric, F}
```

事後共分散行列適応のデフォルト設定。

# フィールド

  * `proposaladaption::BaytesCore.UpdateBool`: 提案ステップの事後共分散が適応されるかどうかのブール値。
  * `metric::BaytesMCMC.MatrixMetric`: 共分散推定メトリック: MDense(), MDiagonal(), MUnit()
  * `shrinkage::Float64`: 等分散の対角行列に向けたシュリンクパラメータ
  * `covariance::Any`: 提案分布の初期共分散行列。'proposaladaption'がUpdateFalseに設定されている場合、サンプリング中は保持される。デフォルトでは初期化されていない。
