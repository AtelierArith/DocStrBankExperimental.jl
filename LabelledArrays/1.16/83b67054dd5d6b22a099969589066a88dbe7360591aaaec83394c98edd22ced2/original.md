```julia
LArray(::Tuple, ::NamedTuple)
LArray(::Tuple, kwargs)
```

The standard constructors for `LArray`.

For example:

```julia
LArray((2, 2), (a = 1, b = 2, c = 3, d = 4))  # need to specify size
LArray((2, 2); a = 1, b = 2, c = 3, d = 4)
```
