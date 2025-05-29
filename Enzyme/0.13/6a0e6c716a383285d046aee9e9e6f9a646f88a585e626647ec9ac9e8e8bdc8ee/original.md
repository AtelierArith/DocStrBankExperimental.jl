```
hvp!(res::X, f::F, x::X, v::X) where {F, X}
```

Compute an in-place Hessian-vector product of an array-input scalar-output function `f`, as evaluated at `x` times the vector `v`. The result will be stored into `res`. The function still allocates and zero's a buffer to store the intermediate gradient, which is not returned to the user.

In other words, compute res .= hessian(f)(x) * v

See [`hvp_and_gradient!`](@ref) for a function to compute both the hvp and the gradient in a single call.

Example:

```jldoctest hvpip; filter = r"([0-9]+\.[0-9]{8})[0-9]+" => s"\1***"
f(x) = sin(x[1] * x[2])

res = Vector{Float64}(undef, 2)
hvp!(res, f, [2.0, 3.0], [5.0, 2.7])

res
# output
2-element Vector{Float64}:
 19.6926882637302
 16.201003759768003
```
