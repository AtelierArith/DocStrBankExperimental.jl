```
missingdata(data::PopData; by::Union{String, Symbol} = "sample")
```

Get missing genotype information in a `PopData`. Specify a mode of operation to return a DataFrame corresponding with that missing information.

#### Modes

  * "sample" - returns a count and percent and list of missing loci per individual (default)
  * "population" - returns a count and percent of missing genotypes per population
  * "locus" - returns a count and percent of missing genotypes per locus
  * "locusxpopulation" - returns a count and percent of missing genotypes per locus per population

### Example:

```
missingdata(@gulfsharks, by = "pop")
```
