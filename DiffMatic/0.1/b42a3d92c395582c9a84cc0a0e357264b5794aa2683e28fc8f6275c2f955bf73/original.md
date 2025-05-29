```
jacobian(expr, wrt::Tensor)
```

Compute the jacobian of `expr` with respect to `wrt`. `expr` must be a column vector and `wrt` a vector. Example:

```jldoctest
@matrix A
@vector x

jacobian(A * x, x)

# output

A¹₅
```
