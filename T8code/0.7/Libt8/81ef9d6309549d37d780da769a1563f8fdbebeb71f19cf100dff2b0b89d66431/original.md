A call-back function used by t8*forest*search for queries. Is called on an element and all queries are checked on that element. All positive queries are passed further down to the children of the element up to leaf elements of the tree. The results of the check are stored in *query_matches*.

# Arguments

  * `forest`:[in] the forest
  * `ltreeid`:[in] the local tree id of the current tree
  * `element`:[in] the element for which the queries are executed
  * `is_leaf`:[in] true if and only if *element* is a leaf element
  * `leaf_elements`:[in] the leaf elements in *forest* that are descendants of *element* (or the element  itself if *is_leaf* is true)
  * `tree_leaf_index`:[in] the local index of the first leaf in *leaf_elements*
  * `queries`:[in] An array of queries that are checked by the function
  * `query_indices`:[in] An array of size_t entries, where each entry is an index of a query in  queries.
  * `query_matches`:[in,out] An array of length *num*active*queries*.  If the element is not a leave must be set to true or false at the i-th index for  each query, specifying whether the element 'matches' the query of the i-th query  index or not. When the element is a leaf we can return before all entries are set.
  * `num_active_queries`:[in] The number of currently active queries (equals the number of entries of  *query_matches* and entries of *query_indices*).
