```
function prep(f::StatsModels.TermOrTerms, inputData::DataFrame;userHints=Dict{Symbol,Any}(),path2ped=[],priorVCV=[])
```

  * `NextGP` relies on `StatsModels.jl` package for model expression (`f`), and fixed effect design matrix generation.
  * Details for the model expression (`f`), and fixed effects coding specifications (e.g., effect or dummy coding) can be found at [`StatsModels.jl`](https://juliastats.org/StatsModels.jl/latest/).
  * Design matrices for random effects are generated either own internal functions or using `StatsModels.jl`s `modelcols`, depending on how user defined the model term in the model.
  * Reads in marker data, and mean-centers the columns.
  * Finally returns lhs vector and rhs matrices.
  * By default:

      * all `Int` rhs variables are made `Categorical`,
      * all `String` rhs variables (also those made `Categorical`) are dummy coded, except those defined by the user in `userHints`,
      * all `Float` rhs variables are centered.
