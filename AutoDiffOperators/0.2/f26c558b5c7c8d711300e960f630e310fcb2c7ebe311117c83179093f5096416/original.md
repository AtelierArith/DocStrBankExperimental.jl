```
with_gradient(f, x, ad::ADSelector)
```

Returns a tuple (f(x), ∇f(x)) with the gradient ∇f(x) of `f` at `x`.

See also [`with_gradient!!(f, δx, x, ad)`](@ref) for the "maybe-in-place" variant of this function.
