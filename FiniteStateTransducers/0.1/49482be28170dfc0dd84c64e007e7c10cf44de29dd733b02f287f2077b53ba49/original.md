`is_deterministic(fst::WFST; get_label=get_ilabel)`

Returns `true` if `fst` is deterministic in the input labels. A input label deterministic WFST must have a single initial state and arcs leaving any state do not share the same input label.

Change the keyword `get_label` to `get_olabel` in order to check determinism in the output labels.
