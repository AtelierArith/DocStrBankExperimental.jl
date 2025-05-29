A Mondrian tree is determined by:

  * `id`: a string to identify the tree
  * `lambda`: the non-negative lifetime parameter
  * `lower`: the lower coordinate of the root cell
  * `upper`: the upper coordinate of the root cell
  * `creation_time`: the time when the root cell was created during sampling
  * `is_split`: whether the root cell is split
  * `split_axis`: the direction in which the root cell is split, if any
  * `split_location`: the location on `split_axis` at which the root cell is split, if any
  * `tree_left`: the left child tree of the root cell, if any
  * `tree_right`: the right child tree of the root cell, if any
