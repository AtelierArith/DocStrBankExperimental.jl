```
with_gradient!!(f, δx, x, ad::ADSelector)
```

Returns a tuple (f(x), ∇f(x)) with the gradient `∇f(x)``of`f`at`x`.

`δx` may or may not be reused/overwritten and returned as `∇f(x)`.

The default implementation falls back to [`with_gradient(f, x, ad)`](@ref), subtypes of `ADSelector` may specialized `with_gradient!!` to provide more efficient implementations.
