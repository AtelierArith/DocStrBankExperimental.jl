```
updatehalo!(A, include_periodic_bc=false)
```

Synchronize the halo regions within each block. This spawns tasks so that each thread/block copies from it's neighbor block's domain into the current block's halo region.

# Arguments

  * `A`: `BlockHaloArray`
  * `include_periodic_bc`: Update the halo regions that are on periodic boundaries
