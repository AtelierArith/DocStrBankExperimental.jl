```
rawview(img::AbstractArray{FixedPoint})
```

returns a "view" of `img` where the values are interpreted in terms of their raw underlying storage. For example, if `img` is an `Array{N0f8}`, the view will act like an `Array{UInt8}`.

See also: [`normedview`](@ref)
