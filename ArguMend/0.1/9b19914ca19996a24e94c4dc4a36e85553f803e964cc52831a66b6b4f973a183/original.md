```
extract_close_matches(key, candidates; n=3, cutoff=0.6)
```

Finds and returns up to `n` close matches from `candidates` for a given `key` based on a similarity ratio. The similarity ratio is calculated using the `similarity_ratio` function, which compares matching subsequences.

# Arguments

  * `key`: The string or sequence for which close matches are sought.
  * `candidates`: An array of strings or sequences against which the `key` is compared.

# Optional keywords

  * `n`: The maximum number of close matches to return (default is 3).
  * `cutoff`: The minimum similarity ratio required for a candidate to be considered a close match (default is 0.6).

# Returns

  * An array of up to `n` candidates that have a similarity ratio above the `cutoff`.

# Examples

```julia
julia> mistyped_kw = "iterations";

julia> candidate_kws = ["niterations", "ncycles_per_iteration", "niterations_per_cycle", "abcdef", "iter"];

julia> extract_close_matches(mistyped_kw, candidate_kws)
["niterations", "niterations_per_cycle"]
```
