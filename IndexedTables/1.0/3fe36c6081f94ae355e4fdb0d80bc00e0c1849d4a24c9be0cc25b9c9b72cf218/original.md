```
map_rows(f, c...)
```

Transform collection `c` by applying `f` to each element. For multiple collection arguments, apply `f` elementwise. Collect output as `Columns` if `f` returns `Tuples` or `NamedTuples` with constant fields, as `Array` otherwise.

# Examples

```
map_rows(i -> (exp = exp(i), log = log(i)), 1:5)
```
