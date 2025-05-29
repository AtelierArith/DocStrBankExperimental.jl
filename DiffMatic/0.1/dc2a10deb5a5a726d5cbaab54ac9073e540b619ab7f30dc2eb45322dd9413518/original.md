```
hessian(expr, wrt::Tensor)
```

Compute the hessian of `expr` with respect to `wrt`. `expr` must be a scalar and `wrt` a vector. Example:

```jldoctest
@matrix A
@vector x

hessian(x' * A * x, x)

# output

A₇⁶ + A⁶₇
```
