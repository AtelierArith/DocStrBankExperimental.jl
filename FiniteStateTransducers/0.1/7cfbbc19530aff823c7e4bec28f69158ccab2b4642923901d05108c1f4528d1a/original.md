`topsort(fst::WFST, i = get_initial(fst); filter=arc->true)`

Requires `fst` to be acyclic.

Returns an equivalent WFST to `fst` which is topologically sorted starting from the `i`-th state.

Modify the `filter` function to perform the operation considering only specific arcs.
