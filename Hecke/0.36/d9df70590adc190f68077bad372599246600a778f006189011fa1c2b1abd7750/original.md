```
class_group(O::AbsSimpleNumFieldOrder; bound = -1,
                      redo = false,
                      GRH = true)   -> FinGenAbGroup, Map
```

Returns a group $A$ and a map $f$ from $A$ to the set of ideals of $O$. The inverse of the map is the projection onto the group of ideals modulo the group of principal ideals.

By default, the correctness is guarenteed only assuming the Generalized Riemann Hypothesis (GRH).

Keyword arguments:

  * `redo`: Trigger a recomputation, thus avoiding the cache.
  * `bound`: When specified, this is used for the bound for the factor base.
  * `GRH`: If `false`, the correctness of the result does not depend on GRH.
