```
nestedmodels(trm::TableRegressionModel{<: LinearModel}; null::Bool = false, <keyword arguments>)
nestedmodels(trm::TableRegressionModel{<: GeneralizedLinearModel}; null::Bool = false, <keyword arguments>)
nestedmodels(model::LinearMixedModel; null::Bool = false, <keyword arguments>)

nestedmodels(::Type{LinearModel}, formula, data; null::Bool = true, <keyword arguments>)
nestedmodels(::Type{GeneralizedLinearModel}, formula, data, distr::UnivariateDistribution, link::Link = canonicallink(d); null::Bool = true, <keyword arguments>)
nestedmodels(::Type{LinearMixedModel}, f::FormulaTerm, tbl; null::Bool = true, wts = [], contrasts = Dict{Symbol, Any}(), verbose::Bool = false, REML::Bool = false)
```

モデルまたは式とデータからネストされたモデルを生成します。

nullモデルは、リンク関数が因子を0にすることを許可しない場合（分母の因子を含む）に、少なくとも1つの因子（切片を含む）を持つモデルになります。

  * `Gamma`のための`InverseLink`
  * `InverseGaussian`のための`InverseSquareLink`
  * `dropcollinear = true`のときに`CholeskyPivoted`でフィッティングされた`LinearModel`

そうでなければ、空のモデルになります。
