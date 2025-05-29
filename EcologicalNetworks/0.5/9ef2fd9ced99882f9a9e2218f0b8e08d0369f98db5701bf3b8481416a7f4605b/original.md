```
make_joint_distribution(N::NT) where {NT<:AbstractEcologicalNetwork}
```

Returns a probability matrix computed from the adjacency or incidence matrix. Raises an error if the matrix contains negative values. Output in bits.
