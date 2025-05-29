Callback function for the partition recursion.

### Parameters

  * `p4est`:[in] The forest to traverse. Its local quadrants are never accessed.
  * `which_tree`:[in] The tree number under consideration.
  * `quadrant`:[in] This quadrant is not from local forest storage, and its user data is undefined. It represents the branch of the forest in the top-down recursion.
  * `pfirst`:[in] The lowest processor that owns part of **quadrant**. Guaranteed to be non-empty.
  * `plast`:[in] The highest processor that owns part of **quadrant**. Guaranteed to be non-empty. If this is equal to **pfirst**, then the recursion will stop for **quadrant**'s branch after this function returns.
  * `point`:[in,out] Pointer to a user-defined point object. If called per-quadrant, this is NULL.

### Returns

If false, the recursion at quadrant is terminated. If true, it continues if **pfirst** < **plast**.
