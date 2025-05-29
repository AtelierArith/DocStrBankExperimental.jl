```
match_sequentially!(dicts::Vector{Dict{Int, Any}}, matcher::IDMatcher; kw...)
```

Match the `dicts`, a vector of dictionaries mapping IDs (integers) to values, according to the given `matcher` by sequentially applying the [`matching_map`](@ref) function to all elements of `dicts` besides the first one.

In the context of Attractors.jl `dicts` are typically dictionaries mapping IDs to attractors (`StateSpaceSet`s), however the function is generic and would work for any values that `matcher` works with.

Return `rmaps`, which is a vector of dictionaries. `rmaps[i]` contains the [`matching_map`](@ref) for `dicts[i+1]`, i.e., the pairs of `old => new` IDs.

## Keyword arguments

  * `pcurve = nothing`: the curve of parameters along which the continuation occured, from which to extract the `p, pprev` values given to [`matching_map`](@ref). See [`global_continuation`](@ref) if you are unsure what this means.
  * `ds = nothing`: propagated to [`matching_map`](@ref).
  * `retract_keys::Bool = true`: If `true` at the end the function will "retract" keys (i.e., make the integers smaller integers) so that all unique IDs are the 1-incremented positive integers. E.g., if the IDs where 1, 6, 8, they will become 1, 2, 3. The special ID -1 is unaffected by this.
  * `use_vanished = false`: If `use_vanised = true`, then IDs (and their corresponding sets) that existed before but have vanished are kept in "memory" when it comes to matching: the current dictionary values (the attractor sets) are compared to the latest instance of all values that have ever existed, each with a unique ID, and get matched to their closest ones. The value of this keyword is obtained from the `matcher`.
