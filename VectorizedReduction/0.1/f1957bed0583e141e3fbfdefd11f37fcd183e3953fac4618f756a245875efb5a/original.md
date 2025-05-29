```
vvminimum(f, A::AbstractArray, dims=:)
```

Compute the minimum value by calling `f` on each element of `A` over the given `dims`.

# Warning

`NaN` values are not handled!
