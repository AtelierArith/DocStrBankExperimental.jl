```julia
struct CentralComposite <: ExperimentalDesign.AbstractResponseSurfaceDesign
```

中心合成デザインをカプセル化します。

  * `matrix::DataFrames.DataFrame`
  * `factors::Tuple`
  * `formula::StatsModels.FormulaTerm`
  * `alpha::Symbol`
  * `face::Symbol`
