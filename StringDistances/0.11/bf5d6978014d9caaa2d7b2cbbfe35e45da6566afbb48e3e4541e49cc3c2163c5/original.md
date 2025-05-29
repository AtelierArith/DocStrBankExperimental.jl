```
compare(s1, s2, dist)
```

return a similarity score between 0 and 1 for the strings `s1` and  `s2` based on the distance `dist`.

### Examples

```julia-repl
julia> compare("martha", "marhta", Levenshtein())
0.6666666666666667
```
