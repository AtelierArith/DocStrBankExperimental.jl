```
lev(s, t)
```

Levenshtein distance for any iterable, not just strings. Implemented from the pseudocode on the Wikipedia [page for Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance).

# Parameters

  * **s** The first iterable in the comparison; can be a string, Array, tuple,   etc., so long as it can be indexed
  * **t** The second iterable in the comparison; can be a string, Array, tuple,   etc., so long as it can be indexed

# Returns

  * The calculated Levenshtein distance between `s` and `t`
