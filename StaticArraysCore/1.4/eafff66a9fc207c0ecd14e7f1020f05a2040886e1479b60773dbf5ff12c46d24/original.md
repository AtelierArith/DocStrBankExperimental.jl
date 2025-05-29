```
MArray{S, T, N, L}(undef)
MArray{S, T, N, L}(x::NTuple{L})
MArray{S, T, N, L}(x1, x2, x3, ...)
```

Construct a statically-sized, mutable array `MArray`. The data may optionally be provided upon construction and can be mutated later. The `S` parameter is a Tuple-type specifying the dimensions, or size, of the array - such as `Tuple{3,4,5}` for a 3×4×5-sized array. The `N` parameter is the dimension of the array; the `L` parameter is the `length` of the array and is always equal to `prod(S)`. Constructors may drop the `L`, `N` and `T` parameters if they are inferrable from the input (e.g. `L` is always inferrable from `S`).

```
MArray{S}(a::Array)
```

Construct a statically-sized, mutable array of dimensions `S` (expressed as a `Tuple{...}`) using the data from `a`. The `S` parameter is mandatory since the size of `a` is unknown to the compiler (the element type may optionally also be specified).
