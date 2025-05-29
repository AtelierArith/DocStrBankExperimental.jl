```
SMatrix{S1, S2, T, L}(x::NTuple{L, T})
SMatrix{S1, S2, T, L}(x1, x2, x3, ...)
```

Construct a statically-sized matrix `SMatrix`. Since this type is immutable, the data must be provided upon construction and cannot be mutated later. The `L` parameter is the `length` of the array and is always equal to `S1 * S2`. Constructors may drop the `L`, `T` and even `S2` parameters if they are inferrable from the input (e.g. `L` is always inferrable from `S1` and `S2`).

```
SMatrix{S1, S2}(mat::Matrix)
```

Construct a statically-sized matrix of dimensions `S1 × S2` using the data from `mat`. The parameters `S1` and `S2` are mandatory since the size of `mat` is unknown to the compiler (the element type may optionally also be specified).
