```
p4est_partition(p4est_, allow_for_coarsening, weight_fn)
```

Equally partition the forest. The partition can be by element count or by a user-defined weight.

The forest will be partitioned between processors such that they have an approximately equal number of quadrants (or sum of weights).

On one process, the function noops and does not call the weight callback. Otherwise, the weight callback is called once per quadrant in order.

### Parameters

  * `p4est`:[in,out] The forest that will be partitioned.
  * `allow_for_coarsening`:[in] Slightly modify partition such that quadrant families are not split between ranks.
  * `weight_fn`:[in] A weighting function or NULL for uniform partitioning. When running with mpisize == 1, never called. Otherwise, called in order for all quadrants if not NULL. A weighting function with constant weight 1 on each quadrant is equivalent to weight_fn == NULL but other constant weightings may result in different uniform partitionings.

### Prototype

```c
void p4est_partition (p4est_t * p4est, int allow_for_coarsening, p4est_weight_t weight_fn);
```
