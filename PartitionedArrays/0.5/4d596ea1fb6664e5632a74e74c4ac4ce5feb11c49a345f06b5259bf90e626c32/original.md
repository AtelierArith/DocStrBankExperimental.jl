```
struct OwnIndices
```

Container for own indices.

# Properties

  * `n_global::Int`: Number of global indices
  * `owner::Int32`: Id of the part that owns these indices
  * `own_to_global::Vector{Int}`: Global ids of the indices owned by this part. `own_to_global[i_own]` is the global id corresponding to the own index number `i_own`.

# Supertype hierarchy

```
OwnIndices <: Any
```
