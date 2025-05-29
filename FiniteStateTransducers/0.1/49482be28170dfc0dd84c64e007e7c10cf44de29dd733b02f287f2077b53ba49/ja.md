`is_deterministic(fst::WFST; get_label=get_olabel)`

Returns `true` if `fst` is deterministic in the output labels. A output label deterministic WFST must have a single initial state and arcs leaving any state do not share the same output label.
