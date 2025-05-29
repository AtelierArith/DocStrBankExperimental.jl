```
sigma_clip!(x, sigma; fill=:clamp, center=median(x), std=std(x))
sigma_clip!(x, sigma_low, sigma_high; fill=:clamp, center=median(x), std=std(x))
```

In-place version of [`sigma_clip`](@ref)

!!! warning
    `sigma_clip!` mutates the element in place and mutation cannot lead to change in type. Please be considerate of your input type, because if you are using `Int64` and we try to clip it to `0.5` an `InexactError` will be thrown.

    To avoid this, we recommend converting to float before clipping, or using [`sigma_clip`](@ref) which does this internally.

