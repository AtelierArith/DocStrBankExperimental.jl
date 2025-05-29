```
p4est_search_partition(p4est_, call_post, quadrant_fn, point_fn, points)
```

Traverse the global partition top-down. We proceed top-down through the partition, identically on all processors except for the results of two user-provided callbacks. The recursion will only go down branches that are split between multiple processors. The callback functions can be used to stop a branch recursion even for split branches. This function offers the option to search for arbitrary user-defined points analogously to p4est*search*local.

!!! note
    Traversing the whole processor partition will be at least O(P), so sensible use of the callback function is advised to cut it short.


### Parameters

  * `p4est`:[in] The forest to traverse. Its local quadrants are never accessed.
  * `call_post`:[in] If true, call quadrant callback both pre and post.
  * `quadrant_fn`:[in] This function controls the recursion, which only continues deeper if this callback returns true for a branch quadrant. It is allowed to set this to NULL.
  * `point_fn`:[in] This function decides per-point whether it is followed down the recursion. Must be non-NULL if **points** are not NULL.
  * `points`:[in] User-provided array of **points** that are passed to the callback **point_fn**. See p4est*search*local for details.

### Prototype

```c
void p4est_search_partition (p4est_t * p4est, int call_post, p4est_search_partition_t quadrant_fn, p4est_search_partition_t point_fn, sc_array_t * points);
```
