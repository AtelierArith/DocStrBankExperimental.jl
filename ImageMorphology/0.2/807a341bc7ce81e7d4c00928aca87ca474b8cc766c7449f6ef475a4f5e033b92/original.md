```
thinning(img::AbstractArray{Bool}; algo::ThinAlgo=GuoAlgo())
```

Applies a binary blob thinning operation to achieve a skeletization of the input image.

See also: [`GuoAlgo`](@ref)
