```julia
    Pad(style::Symbol, lo::Dims, hi::Dims)
```

Construct an instance of [`Pad`](@ref) such that the image is prepended by `lo` pixels  and appended by `hi` pixels  in each dimension.

#### Usage illustration

Use `Pad(:replicate,(1,2),(3,4))` to designate that the top and bottom border should be replicated by one and two pixels, and that the left and right border should be replicated by three and four pixels.

---
