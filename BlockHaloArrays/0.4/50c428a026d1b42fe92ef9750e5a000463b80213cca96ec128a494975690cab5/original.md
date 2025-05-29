```
updateblockhalo!(A::BlockHaloArray, block_id::Integer, include_periodic_bc=false)
```

Copy data from the neighbor block into the current block's halo region

# Arguments

  * `A`: `BlockHaloArray`
  * `block_id::Integer`: Block index
  * `include_periodic_bc`: Update the halo regions that are on periodic boundaries
