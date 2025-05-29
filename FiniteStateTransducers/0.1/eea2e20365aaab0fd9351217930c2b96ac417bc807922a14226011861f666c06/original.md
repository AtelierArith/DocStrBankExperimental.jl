`get_paths(fst::FST, [i = get_initial(fst;single=true)])`

Returns an iterator that generates all of the possible paths of `fst` starting from `i`.

Notice that the `fst` must be acyclic for the algorithm to stop (see [`is_acyclic`](@ref)).
