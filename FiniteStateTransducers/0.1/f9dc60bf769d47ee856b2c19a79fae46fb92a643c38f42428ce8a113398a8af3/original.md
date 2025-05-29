`topsortperm(fst::WFST, i = get_initial(fst); filter=arc->true)`

Requires `fst` to be acyclic.

Returns the topological permutation of states of `fst` starting from the `i`-th state.

Modify the `filter` function to perform the operation considering only specific arcs.
