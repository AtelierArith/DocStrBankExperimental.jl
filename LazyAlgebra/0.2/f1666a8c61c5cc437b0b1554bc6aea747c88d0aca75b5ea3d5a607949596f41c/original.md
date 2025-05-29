```
GeneralMatrix(A)
```

creates a linear mapping whose coefficients are given by a multi-dimensional array `A` and which generalizes the definition of the matrix-vector product without calling `reshape` to change the dimensions.

For instance, assuming that `G = GeneralMatrix(A)` with `A` a regular array, then `y = G*x` requires that the dimensions of `x` match the trailing dimensions of `A` and yields a result `y` whose dimensions are the remaining leading dimensions of `A`, such that `axes(A) = (axes(y)..., axes(x)...)`. Applying the adjoint of `G` as in `y = G'*x` requires that the dimensions of `x` match the leading dimension of `A` and yields a result `y` whose dimensions are the remaining trailing dimensions of `A`, such that `axes(A) = (axes(x)..., axes(y)...)`.

See also: [`reshape`](@ref).
