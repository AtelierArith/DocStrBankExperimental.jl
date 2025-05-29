```
    establish_contour_hierarchy(labels::AbstractArray{<:Integer})
```

Traces the contour of both the outer boundary and hole boundary of each labelled component and stores the hierarichal relationship among the contours in a tree data structure.

# Details

The tree is of type [`LeftChildRightSiblingTree`](https://github.com/JuliaCollections/LeftChildRightSiblingTrees.jl) and you can use the functionality from the [`AbstractTrees.jl`](https://github.com/JuliaCollections/AbstractTrees.jl) package to iterate over it.

Each `Node` of the tree has a `data` field of type [`DigitalContour`](@ref).

The parent/child relationship of the tree reflects the nesting of connected components. If a connected component is wholly contained within another connected component, then its contours will be children of the contours of its surrounding connected component.

# Example

```julia
using ImageComponentAnalysis, TestImages, ImageBinarization, ImageCore, AbstractTrees, Parameters

img = Gray.(testimage("blobs"))
img2 = binarize(img, Otsu())
components = label_components(img2, trues(3,3), 1)
tree = establish_contour_hierarchy(components)

# Iterate over all DigitalContour's in the tree.
for node in PostOrderDFS(tree)
    @unpack id, is_outer, pixels node.data # See Parameters.jl for "@unpack"
    @show id, is_outer, pixels
end
```

# Reference

1. S. Suzuki and K. Abe, “Topological structural analysis of digitized binary images by border following,” Computer Vision, Graphics, and Image Processing, vol. 29, no. 3, p. 396, Mar. 1985.
