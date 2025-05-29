```
MaybeArrayAxes{N}
```

is the type of arguments eligible to specify array axes, that is an `N`-tuple of `MaybeArrayAxis`.

Calling `as_array_axes(x::MaybeArrayAxes{N})` is guaranteed to yield an instance of `ArrayAxes{N}`.
