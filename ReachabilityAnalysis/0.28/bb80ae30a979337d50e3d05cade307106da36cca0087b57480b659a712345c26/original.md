```
Flowpipe{N, RT<:AbstractReachSet{N}, VRT<:AbstractVector{RT}} <: AbstractFlowpipe
```

Type that wraps a flowpipe, which is an iterable collection of reach-sets that behaves like their set union.

### Fields

  * `Xk`  – array of reach-sets
  * `ext` – extension dictionary; field used by extensions

### Notes

The dimension of the flowpipe corresponds to the dimension of the underlying reach-sets; in this type, it is is assumed that the dimension is the same for the different reach-sets.
