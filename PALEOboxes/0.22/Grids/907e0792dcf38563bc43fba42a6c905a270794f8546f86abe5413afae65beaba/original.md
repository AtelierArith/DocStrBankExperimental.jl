```
AbstractSubdomain
```

Defines the relationship between two [`PB.Domain`](@ref)s by mapping indices in one Domain to related indices in the other, eg interior cells adjacent to a boundary.

Concrete subtypes should implement:

[`subdomain_view`](@ref)

[`subdomain_indices`](@ref)
