```
p6est_partition(p6est_, weight_fn)
```

Equally partition the forest.

The forest will be partitioned between processors where they each have an approximately equal number of quadrants.

Note that `p6est`->layers and `p6est`->global*first*layers may change during this call. Address pointers referencing these objects from before [`p6est_partition`](@ref) is called become invalid.

### Parameters

  * `p6est`:[in,out] The forest that will be partitioned.
  * `weight_fn`:[in] A weighting function or NULL for uniform partitioning.

### Prototype

```c
p4est_gloidx_t p6est_partition (p6est_t * p6est, p6est_weight_t weight_fn);
```
