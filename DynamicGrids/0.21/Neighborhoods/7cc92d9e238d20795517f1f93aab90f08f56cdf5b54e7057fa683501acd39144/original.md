```
neighbors(x::Union{Neighborhood,NeighborhoodRule}}) -> iterable
```

Returns an indexable iterator for all cells in the neighborhood, either a `Tuple` of values or a range.

Custom `Neighborhood`s must define this method.
