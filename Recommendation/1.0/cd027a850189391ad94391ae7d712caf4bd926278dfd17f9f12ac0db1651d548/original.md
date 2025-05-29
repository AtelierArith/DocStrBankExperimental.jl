```
Coverage
```

Catalog coverage is a ratio of recommended items among `catalog`, which represents a set of all available items.

```julia
measure(
    metric::Coverage, recommendations::Union{AbstractSet, AbstractVector};
    catalog::Union{AbstractSet, AbstractVector}
)
```
