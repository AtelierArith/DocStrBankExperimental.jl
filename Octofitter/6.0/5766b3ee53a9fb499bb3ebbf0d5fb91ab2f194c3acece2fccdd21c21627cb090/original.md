```
PhotometryLikelihood(
    (band = :Z, phot=15.0, σ_phot=3.),
    (band = :J, phot=13.5, σ_phot=0.5),
    (band = :L, phot=11.0, σ_phot=1.0)
)
```

A likelihood for comparing measured photometry points in one or more  filter bands to data (provided here). Requires the `:band`, `:phot', and`:σ_phot` columns. Can be provided with any Tables.jl compatible data source.
