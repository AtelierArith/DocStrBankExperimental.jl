```
MaybeArrayAxis
```

is the union of types of arguments eligible to define an array axis. This alias is identical to [`IndexRange`](@ref) but has a different purpose.

Calling `as_array_axis(x::MaybeArrayAxis)` is guaranteed to yield an instance of `ArrayAxis`.
