```
p4est_partition_lnodes(p4est_, ghost, degree, partition_for_coarsening)
```

Partition using weights based on the number of nodes assigned to each element in lnodes

### Parameters

  * `p4est`:[in,out] the forest to be repartitioned
  * `ghost`:[in] the ghost layer
  * `degree`:[in] the degree that would be passed to [`p4est_lnodes_new`](@ref)()
  * `partition_for_coarsening`:[in] whether the partition should allow coarsening (i.e. group siblings who might merge)

### Prototype

```c
void p4est_partition_lnodes (p4est_t * p4est, p4est_ghost_t * ghost, int degree, int partition_for_coarsening);
```
