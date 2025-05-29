```
valgrad_func(f, ad::ADSelector)
```

Returns a function `f_∇f` that calculates the value and gradient of `f` at given points, so that `f_∇f(x)` is equivalent to [`with_gradient(f, x, ad)`](@ref).
