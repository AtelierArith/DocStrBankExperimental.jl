```julia
    Pad(both::Dims)
```

Construct an instance of [`Pad`](@ref) with default `:replicate` extrapolation, where the tuple `both` specifies the number of pixels which will be prepended and appended for each dimension.

#### Usage illustration

Use `Pad((5,5))` to designate that the top, bottom, left and right border should be replicated by five pixels.

---
