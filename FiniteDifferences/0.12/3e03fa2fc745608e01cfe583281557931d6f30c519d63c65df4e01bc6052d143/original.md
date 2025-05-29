```
grad(fdm, f, xs...)
```

Compute the gradient of `f` for any `xs` for which [`to_vec`](@ref) is defined.

Return tuple of gradients, one for each argument.
