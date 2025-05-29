```
areas(maxtree::MaxTree) -> Array{Int}
```

Computes the areas of all `maxtree` components.

# Returns

The array of the same shape as the original image. The `i`-th element is the area (in pixels) of the component that is represented by the reference pixel with index `i`.

# See also

[`diameters`](@ref), [`area_opening`](@ref), [`area_closing`](@ref).
