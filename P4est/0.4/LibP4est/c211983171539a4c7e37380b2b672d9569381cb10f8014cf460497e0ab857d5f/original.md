```
p4est_search_all(p4est_, call_post, quadrant_fn, point_fn, points)
```

Perform a top-down search on the whole forest.

This function combines the functionality of p4est*search*local and p4est*search*partition; their documentation applies for the most part.

The recursion proceeds from the root quadrant of each tree until (a) we encounter a remote quadrant that covers only one processor, or (b) we encounter a local leaf quadrant. In other words, we proceed with the recursion into a quadrant's children if (a) the quadrant is split between two or more processors, no matter whether one of them is the calling processor or not, or (b) if the quadrant is on the local processor but we have not reached a leaf yet.

The search can track one or more points, which are abstract placeholders. They are matched against the quadrants traversed using a callback function. The result of the callback function can be used to stop a recursion early. The user determines how a point is interpreted, we only pass it around.

Note that in the remote case (a), we may terminate the recursion even if the quadrant is not a leaf, which we have no means of knowing. Still, this case is sufficient to determine the processor ownership of a point.

!!! note
    This is a very powerful function that can become slow if not used carefully.


!!! note
    As with the two other search functions in this file, calling it once with many points is generally much faster than calling it once for each point. Using multiple points also allows for a per-quadrant termination of the recursion in addition to a more costly per-point termination.


!!! note
    This function works fine when used for the special cases that either the partition or the local quadrants are not of interest. However, in the case of querying only local information we expect that p4est*search*local will be faster since it employs specific local optimizations.


### Parameters

  * `p4est`:[in] The forest to be searched.
  * `call_post`:[in] If true, call quadrant callback both pre and post.
  * `quadrant_fn`:[in] Executed once for each quadrant that is entered. If the callback returns false, this quadrant and its descendants are excluded from the search, and the points in this branch are not queried further. Its **point** argument is always NULL. Callback may be NULL in which case it is ignored.
  * `point_fn`:[in] Executed once for each point that is relevant for a quadrant of the search. If it returns true, the point is tracked further down that branch, else it is discarded from the queries for the children. If **points** is not NULL, this callback must be not NULL. If **points** is NULL, it is not called.
  * `points`:[in] User-defined array of points. We do not interpret a point, just pass it into the callbacks. If NULL, only the **quadrant_fn** callback is executed. If that is NULL, the whole function noops. If not NULL, the **point_fn** is called on its members during the search.

### Prototype

```c
void p4est_search_all (p4est_t * p4est, int call_post, p4est_search_all_t quadrant_fn, p4est_search_all_t point_fn, sc_array_t * points);
```
