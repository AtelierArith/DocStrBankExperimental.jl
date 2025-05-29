Callback function to query the match of a "point" with a quadrant.

This function can be called in two roles: Per-quadrant, in which case the parameter **point** is NULL, or per-point, possibly many times per quadrant.

### Parameters

  * `p4est`:[in] The forest to be queried.
  * `which_tree`:[in] The tree id under consideration.
  * `quadrant`:[in] The quadrant under consideration. This quadrant may be coarser than the quadrants that are contained in the forest (an ancestor), in which case it is a temporary variable and not part of the forest storage. Otherwise, it is a leaf and points directly into the forest storage.
  * `local_num`:[in] If the quadrant is not a leaf, this is < 0. Otherwise it is the (non-negative) index of the quadrant relative to the processor-local storage.
  * `point`:[in] Representation of a "point"; user-defined. If **point** is NULL, the callback may be used to prepare quadrant-related search meta data.

### Returns

If **point** is NULL, true if the search confined to **quadrant** should be executed, false to skip it. Else, true if point may be contained in the quadrant and false otherwise; the return value has no effect on a leaf.
