```julia
struct OptimLHCDesign <: ExperimentalDesign.AbstractRandomDesign
```

  * `matrix::DataFrames.DataFrame`
  * `factors::Tuple`
  * `fitness::Vector{Float64}`
