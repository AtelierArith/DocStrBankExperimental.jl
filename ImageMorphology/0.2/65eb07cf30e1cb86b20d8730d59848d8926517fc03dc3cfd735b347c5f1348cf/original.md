```
MaxTree(image::GenericGrayImage; connectivity=1, rev=false) -> MaxTree
```

Constructs the *max-tree* of the `image`.

# Arguments

  * `connectivity::Integer=1`: defines the pixel neighborhood used to construct the connected components. The value is the maximum number of orthogonal steps to reach a neighbor. In 2D, it is 1 for a 4-neighborhood and 2 for a 8-neighborhood. See [`rebuild!](@ref).
  * `rev::Bool=false`: if `false`, the max-tree is traversed from the darkest (the root node) to the brightest, otherwise it's traversed from the brightest (the root) to the darkest.

# Examples

We create a small sample image (Figure 1 from [4]) and build the max-tree.

```jldoctest; setup = :(using ImageMorphology), filter = r"Array{Int64,2}|Matrix{Int64}"
julia> image = [15 13 16; 12 12 10; 16 12 14]
3×3 Array{Int64,2}:
 15  13  16
 12  12  10
 16  12  14

julia> mtree = MaxTree(image, connectivity=2)
MaxTree{2}(false, [4 2 4; 8 2 8; 2 2 2], [8, 2, 5, 6, 4, 9, 1, 3, 7])
```
