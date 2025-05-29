```
Aggregate(domain, var₁ => agg₁, var₂ => agg₂, ..., varₙ => aggₙ)
Aggregate([g₁, g₂, ..., gₙ], var₁ => agg₁, var₂ => agg₂, ..., varₙ => aggₙ)
```

Aggregate variables `var₁`, `var₂`, ..., `varₙ` over geospatial `domain` using aggregation functions `agg₁`, `agg₂`, ..., `aggₙ`. Alternatively, aggregate variables over geometries `g₁`, `g₂`, ..., `gₙ`. Default aggregation function is `mean` for continuous variables and `first` otherwise.

# Examples

```julia
Aggregate(domain, 1 => last, 2 => maximum)
Aggregate(domain, :a => first, :b => minimum)
Aggregate(domain, "a" => last, "b" => maximum)
Aggregate(geoms, "a" => last, "b" => maximum)
```
