```
GetDeriv(ADmode::Val, F::Function; kwargs...) -> Function
```

Returns a function which computes the scalar derivative of `F` out-of-place via a backend specified by `ADmode`.

Example:

```julia
Derivative = GetDeriv(Val(:ForwardDiff), x->exp(-x^2))
Derivative(5.0)
```

For available backends, see `diff_backends()`.
