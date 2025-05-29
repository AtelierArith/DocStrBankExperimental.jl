Callback function prototype to decide for coarsening.

### Parameters

  * `p8est`:[in] the forest
  * `which_tree`:[in] the tree containing *quadrant*
  * `quadrants`:[in] Pointers to 8 siblings in Morton ordering.

### Returns

nonzero if the quadrants shall be replaced with their parent.
