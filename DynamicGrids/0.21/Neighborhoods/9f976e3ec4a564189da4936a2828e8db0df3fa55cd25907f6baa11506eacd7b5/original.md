```
positions(x::Union{Neighborhood,NeighborhoodRule}}, cellindex::Tuple) -> iterable
```

Returns an indexable iterable, over all cells as `Tuple`s of each index in the main array. Useful in `SetNeighborhoodRule` for setting neighborhood values, or for getting values in an Aux array.
