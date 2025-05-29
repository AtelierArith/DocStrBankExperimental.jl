```
nestedmodels(trm::TableRegressionModel{<: LinearModel}; null::Bool = true, <keyword arguments>)
nestedmodels(trm::TableRegressionModel{<: GeneralizedLinearModel}; null::Bool = true, <keyword arguments>)

nestedmodels(::Type{LinearModel}, formula, data; null::Bool = true, <keyword arguments>)
nestedmodels(::Type{GeneralizedLinearModel}, formula, data, distr::UnivariateDistribution, link::Link = canonicallink(d); null::Bool = true, <keyword arguments>)
```

モデルまたは数式とデータからネストされたモデル `NestedModels` を生成します。

nullモデルは、リンク関数が因子を0にすることを許可しない場合（分母に因子がある場合）や、キーワード引数 `null` が偽である場合（デフォルト値は真）に、少なくとも1つの因子（切片を含む）を持つモデルになります。

  * `InverseLink` は `Gamma` 用
  * `InverseSquareLink` は `InverseGaussian` 用
  * `dropcollinear = true` の場合に `CholeskyPivoted` でフィッティングされた `LinearModel`

それ以外の場合は、空のモデルになります。
