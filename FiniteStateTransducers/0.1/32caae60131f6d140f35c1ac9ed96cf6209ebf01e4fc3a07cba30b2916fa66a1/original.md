`collectpaths(fst::FST, [i = get_initial(fst;first=true)])`

Returns an array containing all of the possible paths of `fst` starting from `i`.

Notice that the `fst` must be acyclic for the algorithm to stop (see [`is_acyclic`](@ref)).
