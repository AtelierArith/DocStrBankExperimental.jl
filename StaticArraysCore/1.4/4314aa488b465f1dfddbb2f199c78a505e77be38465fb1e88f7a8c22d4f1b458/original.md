```
MVector{S,T}(undef)
MVector{S,T}(x::NTuple{S, T})
MVector{S,T}(x1, x2, x3, ...)
```

Construct a statically-sized, mutable vector `MVector`. Data may optionally be provided upon construction, and can be mutated later. Constructors may drop the `T` and `S` parameters if they are inferrable from the input (e.g. `MVector(1,2,3)` constructs an `MVector{3, Int}`).

```
MVector{S}(vec::Vector)
```

Construct a statically-sized, mutable vector of length `S` using the data from `vec`. The parameter `S` is mandatory since the length of `vec` is unknown to the compiler (the element type may optionally also be specified).
