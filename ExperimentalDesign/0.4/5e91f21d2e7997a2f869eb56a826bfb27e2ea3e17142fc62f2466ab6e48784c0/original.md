```julia
struct OptimalDesign <: ExperimentalDesign.AbstractOptimalDesign
```

  * `matrix::DataFrames.DataFrame`
  * `factors::NamedTuple`
  * `formula::StatsModels.FormulaTerm`
  * `selected_experiments::Array{Int64}`
  * `criteria::Dict{Symbol, Float64}`

Contains a  set of candidate experiments,  a target optimality criterion,  and a model prior  formula.  A set  of experiments  that maximizes a  given optimality criterion can selected from a candidate set using the [`kl_exchange`](@ref) algorithm.
