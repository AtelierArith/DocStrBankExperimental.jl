```julia
    Fill(value::T, lo::Dims{N}, hi::Dims{N})
    Fill(value, lo::AbstractVector, hi::AbstractVector)
```

Construct an instance of [`Fill`](@ref) designating a `value` such that the image is prepended by `lo` pixels  and appended by `hi` pixels  in each dimension.

#### Usage illustration

Use `Fill(5,(2,2),(2,2))` to specify a padding of two pixels for the top, bottom, left and right edge with the value five.

Use `Fill(zero(eltype(img))(1,2),(3,4))` to specify a padding of one, two, three and four pixels for the top, left, bottom and right edge respectively using a value of zero with the same type as `img`.

Use `Fill(0,[1,2],[3,4]` to specify a padding of one, two, three and four pixels for the top, left, bottom and right edge respectively with the value zero.

---
