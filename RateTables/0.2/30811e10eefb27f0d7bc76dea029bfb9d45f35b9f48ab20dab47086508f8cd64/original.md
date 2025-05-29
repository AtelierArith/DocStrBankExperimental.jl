```
hmd_rates
```

RateTable providing daily hazard rates for both sexes for several countries. They are derived from annual death probabilities (qₓ's) from the [Human Mortality Database](https://www.mortality.org/)

Segmented by `country ∈ keys(hmd_countries)` and `sex ∈ (:male, :female, :total)`. 

The list of countries codes is given with details in the [`hmd_countries`](@ref) constant. 
