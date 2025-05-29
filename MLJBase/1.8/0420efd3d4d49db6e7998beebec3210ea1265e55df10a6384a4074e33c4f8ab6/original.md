```
flat_values(t::NamedTuple)
```

View a nested named tuple `t` as a tree and return, as a tuple, the values at the leaves, in the order they appear in the original tuple.

```julia-repl
julia> t = (X = (x = 1, y = 2), Y = 3);
julia> flat_values(t)
(1, 2, 3)
```
