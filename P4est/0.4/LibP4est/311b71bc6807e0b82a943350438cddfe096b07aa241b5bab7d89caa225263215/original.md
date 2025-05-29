Callback function prototype to calculate weights for partitioning.

!!! note
    Global sum of weights must fit into a 64bit integer.


### Parameters

  * `p8est`:[in] the forest
  * `which_tree`:[in] the tree containing *quadrant*

### Returns

a 32bit integer >= 0 as the quadrant weight.
