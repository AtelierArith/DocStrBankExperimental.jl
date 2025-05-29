```julia
struct FullFactorial <: ExperimentalDesign.AbstractFactorialDesign
```

Encapsulates  an *explicit*  full factorial  design, where  all experiments  are completely computed  and stored.  Use [`IterableFullFactorial`](@ref)  to obtain an *implicit* factorial  design with arbitrary access to the  elements of a full factorial design.

  * `matrix::DataFrames.DataFrame`
  * `factors::NamedTuple`
  * `formula::StatsModels.FormulaTerm`
