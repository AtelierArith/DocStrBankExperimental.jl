```
rev(val)
```

A wrapper that reverses the order of `isless` comparisons. Useful when sorting by several keys, some forward, some reverse.

# Examples

```julia
sort(..., by=x -> (x.a, rev(x.b), rev(x.c)))
```
