```
GMmodel{RateType, PriorType, ProposalType, ParamType, MethodType, ComponentType, ReporterType}
```

GMモデルの構造。

# フィールド

  * `rates::RateType`: 遷移率。
  * `Gtransitions::Tuple`: G状態遷移のベクトルのタプル。
  * `G::Int`: Gステップの数。
  * `nalleles::Int`: RNAを生成するアレルの数。
  * `rateprior::PriorType`: 率のための事前分布。
  * `proposal::ProposalType`: MCMC提案分布。
  * `fittedparam::ParamType`: フィッティングされる率のインデックス。
