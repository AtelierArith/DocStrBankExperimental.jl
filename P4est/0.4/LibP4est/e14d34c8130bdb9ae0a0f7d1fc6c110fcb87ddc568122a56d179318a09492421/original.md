```
p4est_search_local(p4est_, call_post, quadrant_fn, point_fn, points)
```

Search through the local part of a forest. The search is especially efficient if multiple targets, called "points" below, are searched for simultaneously.

The search runs over all local quadrants and proceeds recursively top-down. For each tree, it may start at the root of that tree, or further down at the root of the subtree that contains all of the tree's local quadrants. Likewise, some intermediate levels in the recursion may be skipped if the processor-local part is contained in a single deeper subtree. The outer loop is thus a depth-first, processor-local forest traversal. Each quadrant in that loop either is a leaf, or a (direct or indirect) strict ancestor of a leaf. On entering a new quadrant, a user-provided quadrant-callback is executed.

As a convenience, the user may provide anonymous "points" that are tracked down the forest. This way one search call may be used for multiple targets. The set of points that potentially matches a given quadrant diminishes from the root down to the leaves: For each quadrant, an inner loop over the potentially matching points executes a point-callback for each candidate that determines whether the point may be a match. If not, it is discarded in the current branch, otherwise it is passed to the next deeper level. The callback is allowed to return true for the same point and more than one quadrant; in this case more than one matching quadrant may be identified. The callback is also allowed to return false for all children of a quadrant that it returned true for earlier. If the point callback returns false for all points relevant to a quadrant, the recursion stops. The points can really be anything, `p4est` does not perform any interpretation, just passes the pointer along to the callback function.

If points are present and the first quadrant callback returned true, we execute it a second time after calling the point callback for all current points. This can be used to gather and postprocess information about the points more easily. If it returns false, the recursion stops.

If the points are a NULL array, they are ignored and the recursion proceeds by querying the per-quadrant callback. If the points are not NULL but an empty array, the recursion will stop immediately!

### Parameters

  * `p4est`:[in] The forest to be searched.
  * `call_post`:[in] If true, call quadrant callback both pre and post.
  * `quadrant_fn`:[in] Executed once when a quadrant is entered, and once when it is left (the second time only if points are present and the first call returned true). This quadrant is always local, if not completely then at least one descendant of it. If the callback returns false, this quadrant and its descendants are excluded from the search recursion. Its **point** argument is always NULL. Callback may be NULL in which case it is ignored.
  * `point_fn`:[in] If **points** is not NULL, must be not NULL. Shall return true for any possible matching point. If **points** is NULL, this callback is ignored.
  * `points`:[in] User-defined array of "points". If NULL, only the **quadrant_fn** callback is executed. If that is NULL, this function noops. If not NULL, the **point_fn** is called on its members during the search.

### Prototype

```c
void p4est_search_local (p4est_t * p4est, int call_post, p4est_search_local_t quadrant_fn, p4est_search_local_t point_fn, sc_array_t * points);
```
