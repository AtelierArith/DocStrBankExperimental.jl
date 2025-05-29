```
struct GhostIndices
```

Container for ghost indices.

# Properties

  * `n_global::Int`: Number of global indices
  * `ghost_to_global::Vector{Int}`: Global ids of the ghost indices in this part. `ghost_to_global[i_ghost]` is the global id corresponding to the ghost index number `i_ghost`.
  * `ghost_to_owner::Vector{Int32}`: Owners of the ghost ids. `ghost_to_owner[i_ghost]`is the id of the owner of the ghost index number `i_ghost`.

# Supertype hierarchy

```
GhostIndices <: Any
```
