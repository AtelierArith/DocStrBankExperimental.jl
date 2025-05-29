```
gradient(expr, wrt::Tensor)
```

Compute the gradient of `expr` with respect to `wrt`. `expr` must be a scalar and `wrt` a vector. Example:

```jldoctest
@matrix A
@vector x

gradient(x' * A * x, x)

# output

x⁴A₄⁶ + A⁶⁵x₅
```
