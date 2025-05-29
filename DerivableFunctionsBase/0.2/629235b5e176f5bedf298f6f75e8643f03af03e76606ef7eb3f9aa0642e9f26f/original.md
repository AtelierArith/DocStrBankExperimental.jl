```
GetMatrixJac(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes the Jacobian of an array-valued function `F` out-of-place via a backend specified by `ADmode`.

Example:

```julia
Jacobian = GetMatrixJac(Val(:ForwardDiff), x->[x[1]^2 x[2]^3; x[1]*x[2] 2])
Jacobian(rand(2))
```

For available backends, see `diff_backends()`.
