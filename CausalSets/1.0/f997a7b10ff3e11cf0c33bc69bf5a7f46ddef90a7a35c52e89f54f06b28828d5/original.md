```
count_atoms_between(causet, i, j[, limit])
```

Count the atoms that lie in the future of `i` and in the past of `j`. The atoms `i` and `j` themselves are not counted. This method should be used preferentially over manually counting atoms with `in_past_of`, as it contains some optimizations for the various causal set types.

If the optional parameter `limit` is given, the function will return `nothing` if the count exceeds `limit`. This is useful for optimization purposes.
