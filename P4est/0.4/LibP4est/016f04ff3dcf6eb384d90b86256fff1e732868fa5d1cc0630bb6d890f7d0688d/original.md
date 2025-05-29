Callback function prototype to initialize the quadrant's user data.

### Parameters

  * `p4est`:[in] the forest
  * `which_tree`:[in] the tree containing *quadrant*
  * `quadrant`:[in,out] the quadrant to be initialized: if data_size > 0, the data to be initialized is at *quadrant*->p.user*data; otherwise, the non-pointer user data (such as *quadrant*->p.user*int) can be initialized
