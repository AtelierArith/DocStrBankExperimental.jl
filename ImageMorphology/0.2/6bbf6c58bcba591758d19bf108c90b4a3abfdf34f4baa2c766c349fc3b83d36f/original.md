```
diameters(maxtree::MaxTree) -> Array{Int}
```

Computes the "diameters" of all `maxtree` components.

"Diameter" of the *max-tree* connected component is the length of the widest side of the component's bounding box.

# Returns

The array of the same shape as the original image. The `i`-th element is the "diameter" of the component that is represented by the reference pixel with index `i`.

# See also

[`boundingboxes`](@ref), [`areas`](@ref), [`diameter_opening`](@ref), [`diameter_closing`](@ref).
