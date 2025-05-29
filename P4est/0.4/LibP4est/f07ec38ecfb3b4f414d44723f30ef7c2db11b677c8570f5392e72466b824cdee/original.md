```
p4est_partition_ext(p4est_, partition_for_coarsening, weight_fn)
```

Repartition the forest.

The forest is partitioned between processors such that each processor has an approximately equal number of quadrants (or weight).

### Parameters

  * `p4est`:[in,out] The forest that will be partitioned.
  * `partition_for_coarsening`:[in] If true, the partition is modified to allow one level of coarsening.
  * `weight_fn`:[in] A weighting function or NULL for uniform partitioning. A weighting function with constant weight 1 on each quadrant is equivalent to weight_fn == NULL but other constant weightings may result in different uniform partitionings.

### Returns

The global number of shipped quadrants

### Prototype

```c
p4est_gloidx_t p4est_partition_ext (p4est_t * p4est, int partition_for_coarsening, p4est_weight_t weight_fn);
```
