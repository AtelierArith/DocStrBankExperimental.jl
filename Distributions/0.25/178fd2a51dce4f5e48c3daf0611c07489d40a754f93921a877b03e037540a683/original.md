```
product_distribution(dists::NamedTuple{K,Tuple{Vararg{Distribution}}}) where {K}
```

Create a distribution of `NamedTuple`s as a product distribution of independent named distributions.

The function falls back to constructing a [`ProductNamedTupleDistribution`](@ref) distribution but specialized methods can be defined.
