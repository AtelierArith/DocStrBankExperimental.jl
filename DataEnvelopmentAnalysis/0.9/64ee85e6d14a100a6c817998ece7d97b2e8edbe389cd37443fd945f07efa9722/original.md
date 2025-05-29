```
efficiency(model::AbstractEconomicDEAModel)
```

Return efficiency scores of an economic DEA model.

# Optional Arguments

  * `type=Economic`: type of efficiency scores to return.

Type specification:

  * `:Economic`: returns economic efficiency of the model.
  * `:Technical`: returns technical efficiency.
  * `:Allocative`: returns allocative efficiency.

Some models also allow these types:

  * `:CRS`: returns technical efficiency under constant returns to scale.
  * `:VRS`: returns technical efficiency under variable returns to scale.
  * `:Scale`: returns scale efficiency.
