```
to_egm2008!(table)
```

Converts ellipsoid heights to geoid heights using the EGM2008 geoid model. Assumes a table as generated from [`points`](@ref) with columns `:latitude`, `:longitude`, and `:height`. Will overwrite the `:height` column with the geoid height.
