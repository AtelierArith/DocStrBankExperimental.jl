```
function derivation_heuristic(::TopDownIterator, indices::Vector{Int})
```

Returns a sorted sublist of the `indices`, based on which rules are most promising to fill a hole. The underlying solver can change the order within a Hole's domain. We sort the domain to make the enumeration order explicit and more predictable. 
