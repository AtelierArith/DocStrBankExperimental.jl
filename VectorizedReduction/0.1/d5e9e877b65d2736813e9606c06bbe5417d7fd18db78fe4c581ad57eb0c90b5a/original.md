```
vtmaximum(f, A::AbstractArray, dims=:)
```

Compute the maximum value by calling `f` on each element of `A` over the given `dims`.

# Warning

`NaN` values are not handled!
