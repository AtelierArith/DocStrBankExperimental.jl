```
extract_results(post_mod::Modification, config, data) -> results
```

One of the main steps in [`e4st_post`](@ref).  Extract results (or compute new ones) from `data` (the full set of `data` deserialized from an E4ST run).  This will get stored into an `OrderedDict` mapping `sim_name` to `results`.  See [`combine_results`](@ref) for the next step.

Note that we do this to prevent excessive memory usage.  If [`e4st_post`](@ref) is run with a large number of simulations, storing the entire set of `data` in memory for all of them may cost too much RAM.
