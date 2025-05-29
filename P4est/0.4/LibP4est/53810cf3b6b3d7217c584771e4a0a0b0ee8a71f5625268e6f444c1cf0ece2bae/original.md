```
p6est_partition_ext(p6est_, partition_for_coarsening, weight_fn)
```

Repartition the forest.

The forest is partitioned between processors such that each processor has an approximately equal number of quadrants (or weight).

### Parameters

  * `p6est`:[in,out] The forest that will be partitioned.
  * `partition_for_coarsening`:[in] If true, the partition is modified to allow one level of coarsening.
  * `weight_fn`:[in] A weighting function or NULL for uniform partitioning.

### Returns

The global number of shipped quadrants

### Prototype

```c
p4est_gloidx_t p6est_partition_ext (p6est_t * p6est, int partition_for_coarsening, p6est_weight_t weight_fn);
```
