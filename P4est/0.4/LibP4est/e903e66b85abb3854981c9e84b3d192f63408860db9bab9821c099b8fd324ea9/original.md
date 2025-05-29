Callback function prototype to decide for coarsening.

### Parameters

  * `p4est`:[in] the forest
  * `which_tree`:[in] the tree containing *quadrant*
  * `quadrants`:[in] Pointers to 4 siblings in Morton ordering.

### Returns

nonzero if the quadrants shall be replaced with their parent.
