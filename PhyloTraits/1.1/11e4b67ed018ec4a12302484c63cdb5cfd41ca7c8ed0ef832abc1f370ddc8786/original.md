```
RateVariationAcrossSites(rvsymbol::Symbol, ncategories::Int=4)
```

Default model for rate variation across site, specified by a symbol:

  * `:noRV` for no rate variation
  * `:G` or `:Gamma` for gamma-distributed rates
  * `:I` or `:Inv` for two categories: invariable and variable
  * `:GI` or `:GI` for both.
