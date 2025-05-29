```julia
struct CentralComposite <: ExperimentalDesign.AbstractResponseSurfaceDesign
```

Encapsulates a central composite design.

  * `matrix::DataFrames.DataFrame`
  * `factors::Tuple`
  * `formula::StatsModels.FormulaTerm`
  * `alpha::Symbol`
  * `face::Symbol`
