```
searchdists!(neighbors, distances, pₒ, method; mask=nothing)
```

Update `neighbors` and `distances` of point `pₒ` using bounded search `method` and return number of neighbors found. Optionally, specify a `mask` for all indices of the domain.

See [`BoundedNeighborSearchMethod`](@ref) for additional details.
