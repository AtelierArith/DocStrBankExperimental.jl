```
MAX_SUBGNUM :: ImmutableDict
```

An immutable dictionary with values `v::Int` and keys `k::Tuple{Int,Int}`, where `v` is the number of distinct subperiodic group types for a given key `k = (D,P)` describing a subperiodic group of dimensionality `D` and periodicity `P`:

  * layer groups: `(D,P) = (3,2)`
  * rod groups: `(D,P) = (3,1)`
  * frieze groups: `(D,P) = (2,1)`
