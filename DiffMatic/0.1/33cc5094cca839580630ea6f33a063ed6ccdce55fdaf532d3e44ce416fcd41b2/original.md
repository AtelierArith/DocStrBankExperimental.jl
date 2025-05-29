```
derivative(expr, wrt::Tensor)
```

Compute the derivative of `expr` with respect to `wrt`. Example:

```jldoctest
@matrix A
@vector x

derivative(x' * x, x)

# output

2x₄
```
