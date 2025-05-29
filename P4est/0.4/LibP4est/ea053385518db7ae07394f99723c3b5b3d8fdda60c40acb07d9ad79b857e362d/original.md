```
p8est_lnodes_rank
```

The structure stored in the sharers array.

shared_nodes is a sorted array of [`p4est_locidx_t`](@ref) that indexes into local nodes. The shared_nodes array has a contiguous (or empty) section of nodes owned by the current rank. shared_mine_offset and shared_mine_count identify this section by indexing the shared_nodes array, not the local nodes array. owned_offset and owned_count define the section of local nodes that is owned by the listed rank (the section may be empty). For the current process these coincide with those in [`p8est_lnodes_t`](@ref).
