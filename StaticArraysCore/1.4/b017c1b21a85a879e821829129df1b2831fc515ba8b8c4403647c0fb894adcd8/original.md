```
SVector{S, T}(x::NTuple{S, T})
SVector{S, T}(x1, x2, x3, ...)
```

Construct a statically-sized vector `SVector`. Since this type is immutable, the data must be provided upon construction and cannot be mutated later. Constructors may drop the `T` and `S` parameters if they are inferrable from the input (e.g. `SVector(1,2,3)` constructs an `SVector{3, Int}`).

```
SVector{S}(vec::Vector)
```

Construct a statically-sized vector of length `S` using the data from `vec`. The parameter `S` is mandatory since the length of `vec` is unknown to the compiler (the element type may optionally also be specified).
