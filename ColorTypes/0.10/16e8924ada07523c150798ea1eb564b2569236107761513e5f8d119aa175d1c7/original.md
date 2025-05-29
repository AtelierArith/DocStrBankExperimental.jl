```
CF = floattype(C::Type)
```

Promote storage data type of colorant type `C` to `AbstractFloat` while keeping the `base_colorant_type` the same.

!!! info
    Non-parametric colorants will be promoted to corresponding parametric colorants. For example, `floattype(RGB24) == RGB{Float32}`.

