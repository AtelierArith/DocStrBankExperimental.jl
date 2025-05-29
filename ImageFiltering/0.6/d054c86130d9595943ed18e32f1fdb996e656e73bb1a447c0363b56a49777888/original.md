```julia
    Pad(style::Symbol, m, n, ...)
    Pad(style::Symbol, (m,n))
```

Construct an instance of [`Pad`](@ref) such that the image is prepended and appended symmetrically with `m` pixels at the lower and upper edge of dimension 1, `n` pixels for dimension 2, and so forth.

#### Usage illustration

Use `Pad(:replicate,2,4)` to designate that the top and bottom border should be replicated by two pixels, and the left and right border by four pixels.

Use `Pad(:circular,(0,3))` to designate that the top and bottom border should not be padded, and that the left and right border should wrap around by three pixels.

---
