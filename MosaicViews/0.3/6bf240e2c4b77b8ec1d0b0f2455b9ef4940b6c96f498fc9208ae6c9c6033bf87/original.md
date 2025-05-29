```
MosaicView(A::AbstractArray)
```

Create a two dimensional "view" of the three or four dimensional array `A`. The resulting `MosaicView` will display the data in `A` such that it emulates using `vcat` for all elements in the third dimension of `A`, and `hcat` for all elements in the fourth dimension of `A`.

For example, if `size(A)` is `(2,3,4)`, then the resulting `MosaicView` will have the size `(2*4,3)` which is `(8,3)`. Alternatively, if `size(A)` is `(2,3,4,5)`, then the resulting size will be `(2*4,3*5)` which is `(8,15)`.

Another way to think about this is that `MosaicView` creates a mosaic of all the individual matrices enumerated in the third (and optionally fourth) dimension of the given 3D or 4D array `A`. This can be especially useful for creating a single composite image from a set of equally sized images.

```@jldoctest
julia> using MosaicViews

julia> A = [(k+1)*l-1 for i in 1:2, j in 1:3, k in 1:2, l in 1:2]
2×3×2×2 Array{Int64,4}:
[:, :, 1, 1] =
 1  1  1
 1  1  1

[:, :, 2, 1] =
 2  2  2
 2  2  2

[:, :, 1, 2] =
 3  3  3
 3  3  3

[:, :, 2, 2] =
 5  5  5
 5  5  5

julia> MosaicView(A)
4×6 MosaicViews.MosaicView{Int64,4,Array{Int64,4}}:
 1  1  1  3  3  3
 1  1  1  3  3  3
 2  2  2  5  5  5
 2  2  2  5  5  5
```
