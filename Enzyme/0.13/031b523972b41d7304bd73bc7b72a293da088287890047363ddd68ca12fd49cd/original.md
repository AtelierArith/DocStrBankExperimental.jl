```
hvp_and_gradient!(res::X, grad::X, f::F, x::X, v::X) where {F, X}
```

Compute an in-place Hessian-vector product of an array-input scalar-output function `f`, as evaluated at `x` times the vector `v` as well as the gradient, storing the gradient into `grad`. Both the hessian vector product and the gradient can be computed together more efficiently than computing them separately.

The result will be stored into `res`. The gradient will be stored into `grad`.

In other words, compute res .= hessian(f)(x) * v  and grad .= gradient(Reverse, f)(x)

Example:

```jldoctest hvp_and_gradient; filter = r"([0-9]+\.[0-9]{8})[0-9]+" => s"\1***"
f(x) = sin(x[1] * x[2])

res = Vector{Float64}(undef, 2)
grad = Vector{Float64}(undef, 2)
hvp_and_gradient!(res, grad, f, [2.0, 3.0], [5.0, 2.7])

res
grad
# output
2-element Vector{Float64}:
 2.880510859951098
 1.920340573300732
```
