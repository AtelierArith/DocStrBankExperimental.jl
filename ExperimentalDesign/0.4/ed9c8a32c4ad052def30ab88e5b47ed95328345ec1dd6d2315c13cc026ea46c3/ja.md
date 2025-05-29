```julia
struct BoxBehnken <: ExperimentalDesign.AbstractResponseSurfaceDesign
```

応答面法のためのボックス・ベンケン設計。

  * `matrix::DataFrames.DataFrame`
  * `factors::Tuple`
  * `formula::StatsModels.FormulaTerm`
