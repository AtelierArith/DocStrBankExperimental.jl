```
normedview([T], img::AbstractArray{Unsigned})
```

returns a "view" of `img` where the values are interpreted in terms of `Normed` number types. For example, if `img` is an `Array{UInt8}`, the view will act like an `Array{N0f8}`.  Supply `T` if the element type of `img` is `UInt16`, to specify whether you want a `N6f10`, `N4f12`, `N2f14`, or `N0f16` result.

See also: [`rawview`](@ref)
