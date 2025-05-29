```julia
struct BoxBehnken <: ExperimentalDesign.AbstractResponseSurfaceDesign
```

Box-Behnken design for response surface methodology.

  * `matrix::DataFrames.DataFrame`
  * `factors::Tuple`
  * `formula::StatsModels.FormulaTerm`
