```
ReachSet{N, ST<:LazySet{N}} <: AbstractLazyReachSet{N}
```

Type that wraps a reach-set using a `LazySet` as underlying representation.

### Fields

  * `X`  – set
  * `Δt` – time interval

### Notes

A `ReachSet` is a struct representing (an approximation of) the reachable states for a given time interval. The type of the representation is `ST`, which may be any subtype LazySet. For efficiency reasons, `ST` should be concretely typed.

By assumption the coordinates in this reach-set are associated to the integers `1, …, n`. The function `vars` returns such tuple.
