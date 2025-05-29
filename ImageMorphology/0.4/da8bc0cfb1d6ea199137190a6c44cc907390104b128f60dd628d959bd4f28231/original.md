```
boundingboxes(maxtree::MaxTree) -> Array{NTuple{2, CartesianIndex}}
```

Computes the minimal bounding boxes of all `maxtree` components.

# Returns

The array of the same shape as the original image. The `i`-th element is the tuple of the minimal and maximal cartesian indices for the bounding box of the component that is represented by the reference pixel with index `i`.

# See also

[`diameters`](@ref).
