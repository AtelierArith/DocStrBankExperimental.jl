```
Duplicated(x, ∂f_∂x)
```

Mark a function argument `x` of [`autodiff`](@ref Enzyme.autodiff) as duplicated, Enzyme will auto-differentiate in respect to such arguments, with `dx` acting as an accumulator for gradients (so $\partial f / \partial x$ will be *added to*) `∂f_∂x`.
