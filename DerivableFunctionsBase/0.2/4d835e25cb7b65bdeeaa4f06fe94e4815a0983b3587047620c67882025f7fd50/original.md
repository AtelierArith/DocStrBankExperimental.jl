```
GetJac(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes the Jacobian of `F` out-of-place via a backend specified by `ADmode`.

Example:

```julia
Jacobian = GetJac(Val(:ForwardDiff), x->[x[1]^2, -x[2]^3, x[1]*x[2]])
Jacobian(rand(2))
```

For available backends, see `diff_backends()`.
