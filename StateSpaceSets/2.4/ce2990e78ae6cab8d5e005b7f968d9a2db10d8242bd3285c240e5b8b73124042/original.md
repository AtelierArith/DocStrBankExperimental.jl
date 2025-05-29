```
orthonormal([T,] D, k) -> ws
```

Return a matrix `ws` with `k` columns, each being an `D`-dimensional orthonormal vector.

`T` is the return type and can be either `SMatrix` or `Matrix`. If not given, it is `SMatrix` if `D*k < 100`, otherwise `Matrix`.
