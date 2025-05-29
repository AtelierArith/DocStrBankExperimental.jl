```
struct LocalIndices
```

Container for arbitrary local indices.

# Properties

  * `n_global::Int`: Number of global indices.
  * `owner::Int32`: Id of the part that stores the local indices
  * `local_to_global::Vector{Int}`:  Global ids of the local indices in this part.  `local_to_global[i_local]` is the global id corresponding to the local index number `i_local`.
  * `local_to_owner::Vector{Int32}`: Owners of the local ids. `local_to_owner[i_local]`is the id of the owner of the local index number `i_local`.

# Supertype hierarchy

```
LocalIndices <: AbstractLocalIndices
```
