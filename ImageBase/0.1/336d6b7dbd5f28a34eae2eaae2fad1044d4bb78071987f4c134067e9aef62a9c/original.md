```
varfinite(A; kwargs...)
```

Compute the variance of `A`, ignoring any non-finite values.

The supported `kwargs` are those of `sum(f, A; kwargs...)`.

!!! note
    This function can produce a seemingly suprising result if the input array is an RGB image. To make it more clear, the implementation is made so that `varfinite(img) ≈ varfinite(RGB.(img))` holds for any gray-scale image. See also https://github.com/JuliaGraphics/ColorVectorSpace.jl#abs-and-abs2 for more information.

