A call-back function used by t8*forest*search describing a search-criterion. Is called on an element and the  search criterion should be checked on that element. Return true if the search criterion is met, false otherwise.

# Arguments

  * `forest`:[in] the forest
  * `ltreeid`:[in] the local tree id of the current tree
  * `element`:[in] the element for which the search criterion is checked.
  * `is_leaf`:[in] true if and only if *element* is a leaf element
  * `leaf_elements`:[in] the leaf elements in *forest* that are descendants of *element* (or the element  itself if *is_leaf* is true)
  * `tree_leaf_index`:[in] the local index of the first leaf in *leaf_elements*

# Returns

non-zero if the search criterion is met, zero otherwise.
