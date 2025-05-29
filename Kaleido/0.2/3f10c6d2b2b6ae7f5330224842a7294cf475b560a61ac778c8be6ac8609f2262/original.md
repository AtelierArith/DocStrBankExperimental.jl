```
nullsetter :: Setter
```

A setter that does nothing; i.e., `set(x, nullsetter, y) === x` for any `x` and `y`.

# Examples

```jldoctest
julia> using Setfield, Kaleido

julia> set(1, nullsetter, 2)
1
```
