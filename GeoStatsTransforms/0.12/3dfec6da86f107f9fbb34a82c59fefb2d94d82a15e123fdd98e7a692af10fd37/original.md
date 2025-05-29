```
UniqueCoords(var₁ => agg₁, var₂ => agg₂, ..., varₙ => aggₙ)
```

Retain locations in data with unique coordinates.

Duplicates of a variable `varᵢ` are aggregated with aggregation function `aggᵢ`. If an aggregation function  is not defined for variable `varᵢ`, the default aggregation  function will be used. Default aggregation function is `mean` for continuous variables and `first` otherwise.

# Examples

```julia
UniqueCoords(1 => last, 2 => maximum)
UniqueCoords(:a => first, :b => minimum)
UniqueCoords("a" => last, "b" => maximum)
```
