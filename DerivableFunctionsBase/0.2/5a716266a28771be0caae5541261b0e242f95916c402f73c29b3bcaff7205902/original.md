```
GetGrad(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes the gradient of `F` out-of-place via a backend specified by `ADmode`.

Example:

```julia
Gradient = GetGrad(Val(:ForwardDiff), x->x[1]^2 - x[2]^3)
Gradient(rand(2))
```

For available backends, see `diff_backends()`.
