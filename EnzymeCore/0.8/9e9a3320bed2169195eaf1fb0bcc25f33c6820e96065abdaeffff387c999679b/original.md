```
BatchDuplicated(x, ∂f_∂xs)
```

Like [`Duplicated`](@ref), except contains several shadows to compute derivatives for all at once. Argument `∂f_∂xs` should be a tuple of the several values of type `x`.
