```
compute_extreme_point(lmo::ProductLMO, direction::AbstractArray; direction_indices, storage=similar(direction))
```

Extreme point computation, with a direction array and `direction_indices` provided such that: `direction[direction_indices[i]]` is passed to the i-th LMO. If no `direction_indices` are provided, the direction array is sliced along the last dimension and such that: `direction[:, ... ,:, i]` is passed to the i-th LMO. The result is stored in the optional `storage` container.

All keyword arguments are passed to all LMOs.
