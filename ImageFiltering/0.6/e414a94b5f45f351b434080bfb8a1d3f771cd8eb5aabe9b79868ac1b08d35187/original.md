```julia
    Fill(value::T, both::Dims{N})
```

Construct an instance of [`Fill`](@ref) designating a `value`  and a tuple `both` which stipulates the number of row and columns which will be prepended and appended to the image.

#### Usage illustration

Use `Fill(0,(5,10))` to stipulate a padding of five pixels for the top and left edge, and a padding of ten pixels for the bottom and right edge with a value of zero.

---
