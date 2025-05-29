```
globalindices(A::BlockHaloArray, block_index, local_indices) -> global_indices
```

Given a block index and local coordinates, return the global indices

# Example

```
julia> globalindices(A, 2, (3, 4)) -> (8, 10)
```
