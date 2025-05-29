```
align(xs::AbstractArray, sa::ScaledArrOrSub)
```

Convert `xs` into a [`ScaledArray`](@ref) with a `pool` that has the same first element and step size as the `pool` from `sa`.
