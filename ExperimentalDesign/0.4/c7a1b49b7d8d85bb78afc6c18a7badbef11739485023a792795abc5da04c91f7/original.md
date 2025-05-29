```julia
struct PlackettBurman <: ExperimentalDesign.AbstractScreeningDesign
```

Encapsulates  a  Plackett-Burman  screening  design  constructed  using  Paley's method.  Factor  levels are  encoded as  `:high` and  `:low` symbols,  and extra dummy variables, possibly  aliasing interactions between factors,  will be added to pad a design.

  * `matrix::DataFrames.DataFrame`
  * `factors::Tuple`
  * `dummy_factors::Tuple`
  * `formula::StatsModels.FormulaTerm`
