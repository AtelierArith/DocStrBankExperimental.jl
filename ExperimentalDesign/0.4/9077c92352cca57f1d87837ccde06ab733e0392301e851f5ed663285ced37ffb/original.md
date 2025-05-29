```julia
struct DesignDistribution
```

  * `factors::NamedTuple`
  * `formula::StatsModels.FormulaTerm`

Encapsulates one or more `Distribution`s, generating random designs.  Receives a `NamedTuple`  of  factor names  associated  with  `Distribution`s from  the  the *Distributions* package.   After instantiating a `DesignDistribution`,  you must request   samples   from   it    using   [`rand`](@ref),   which   generates   a [`RandomDesign`](@ref)
