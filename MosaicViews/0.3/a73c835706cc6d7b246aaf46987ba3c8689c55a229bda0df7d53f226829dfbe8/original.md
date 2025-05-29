```
mosaicview(A::AbstractArray;
           [fillvalue=<zero unit>], [npad=0],
           [nrow], [ncol], [rowmajor=false]) -> MosaicView
mosaicview(As::AbstractArray...; kwargs...)
mosaicview(As::Union{Tuple, AbstractVector}; kwargs...)
```

Create a two dimensional "view" from array `A`.

The resulting [`MosaicView`](@ref) will display all the matrix slices of the first two dimensions of `A` arranged as a single large mosaic (in the form of a matrix).

# Arguments

In contrast to using the constructor of [`MosaicView`](@ref) directly, the function `mosaicview` also allows for a couple of convenience keywords. A typical use case would be to create an image mosaic from a set of input images.

  * The parameter `fillvalue` defines the value that that should be used for empty space. This can be padding caused by `npad`, or empty mosaic tiles in case the number of matrix slices in `A` is smaller than `nrow*ncol`.
  * The parameter `npad` defines the empty padding space between adjacent mosaic tiles. This can be especially useful if the individual tiles (i.e. matrix slices in `A`) are images that should be visually separated by some grid lines.
  * The parameters `nrow` and `ncol` can be used to choose the number of tiles in row and/or column direction the mosaic should be arranged in. Note that it suffices to specify one of the two parameters, as the other one can be inferred accordingly. The default in case none of the two are specified is `nrow = size(A,3)`.
  * If `rowmajor` is set to `true`, then the slices will be arranged left-to-right-top-to-bottom, instead of top-to-bottom-left-to-right (default). The layout only differs in non-trivial cases, i.e., when `nrow != 1` and `ncol != 1`.

!!! tip
    This function is not type stable and should only be used if performance is not a priority. To achieve optimized performance, you need to manually construct a [`MosaicView`](@ref).


# Examples

The simplest usage is to `cat` two arrays of the same dimension.

```julia-repl
julia> A1 = fill(1, 3, 1)
3×1 Array{Int64,2}:
 1
 1
 1

julia> A2 = fill(2, 1, 3)
1×3 Array{Int64,2}:
 2  2  2

julia> mosaicview(A1, A2)
6×3 MosaicView{Int64,4, ...}:
 0  1  0
 0  1  0
 0  1  0
 0  0  0
 2  2  2
 0  0  0

julia> mosaicview(A1, A2; center=false)
 6×3 MosaicView{Int64,4, ...}:
  1  0  0
  1  0  0
  1  0  0
  2  2  2
  0  0  0
  0  0  0
```

Other keyword arguments can be useful to get a nice looking results.

```julia-repl
julia> using MosaicViews

julia> A = [k for i in 1:2, j in 1:3, k in 1:5]
2×3×5 Array{Int64,3}:
[:, :, 1] =
 1  1  1
 1  1  1

[:, :, 2] =
 2  2  2
 2  2  2

[:, :, 3] =
 3  3  3
 3  3  3

[:, :, 4] =
 4  4  4
 4  4  4

[:, :, 5] =
 5  5  5
 5  5  5

julia> mosaicview(A, ncol=2)
6×6 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  4  4  4
 1  1  1  4  4  4
 2  2  2  5  5  5
 2  2  2  5  5  5
 3  3  3  0  0  0
 3  3  3  0  0  0

julia> mosaicview(A, nrow=2)
4×9 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  3  3  3  5  5  5
 1  1  1  3  3  3  5  5  5
 2  2  2  4  4  4  0  0  0
 2  2  2  4  4  4  0  0  0

julia> mosaicview(A, nrow=2, rowmajor=true)
4×9 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  2  2  2  3  3  3
 1  1  1  2  2  2  3  3  3
 4  4  4  5  5  5  0  0  0
 4  4  4  5  5  5  0  0  0

julia> mosaicview(A, nrow=2, npad=1, rowmajor=true)
5×11 MosaicViews.MosaicView{Int64,4,...}:
 1  1  1  0  2  2  2  0  3  3  3
 1  1  1  0  2  2  2  0  3  3  3
 0  0  0  0  0  0  0  0  0  0  0
 4  4  4  0  5  5  5  0  0  0  0
 4  4  4  0  5  5  5  0  0  0  0

julia> mosaicview(A, fillvalue=-1, nrow=2, npad=1, rowmajor=true)
5×11 MosaicViews.MosaicView{Int64,4,...}:
  1   1   1  -1   2   2   2  -1   3   3   3
  1   1   1  -1   2   2   2  -1   3   3   3
 -1  -1  -1  -1  -1  -1  -1  -1  -1  -1  -1
  4   4   4  -1   5   5   5  -1  -1  -1  -1
  4   4   4  -1   5   5   5  -1  -1  -1  -1
```
