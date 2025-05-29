```
p8est_partition_lnodes(p8est_, ghost, degree, partition_for_coarsening)
```

Partition using weights based on the number of nodes assigned to each element in lnodes

### Parameters

  * `p8est`:[in,out] the forest to be repartitioned
  * `ghost`:[in] the ghost layer
  * `degree`:[in] the degree that would be passed to [`p8est_lnodes_new`](@ref)()
  * `partition_for_coarsening`:[in] whether the partition should allow coarsening (i.e. group siblings who might merge)

### Prototype

```c
void p8est_partition_lnodes (p8est_t * p8est, p8est_ghost_t * ghost, int degree, int partition_for_coarsening);
```
