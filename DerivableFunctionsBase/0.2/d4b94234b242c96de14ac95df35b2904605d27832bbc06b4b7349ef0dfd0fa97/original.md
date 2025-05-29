```
GetDoubleJac(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes the Jacobian of the Jacobian for a vector-valued function `F` out-of-place via a backend specified by `ADmode`.

Example:

```julia
DoubleJacobian = GetDoubleJac(Val(:ForwardDiff), x->[x[1]^2, x[1]*x[2]^3])
DoubleJacobian(rand(2))
```

For available backends, see `diff_backends()`.
