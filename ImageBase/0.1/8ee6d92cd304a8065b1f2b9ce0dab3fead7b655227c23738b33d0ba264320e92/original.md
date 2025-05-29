```
restrict(img[, dims]) -> imgr
```

Reduce the size of `img` by approximately two-fold along the dimensions listed in `dims`, or all spatial coordinates if `dims` is not specified.

# Output

The type of output array `imgr` depends on the input type:

  * If `img` is an `OffsetArray`, then output array `imgr` will also be an `OffsetArray`.
  * If `img` is not an `OffsetArray`, then output array `imgr` will be an `Array` type even if it has offset indices.

The size of `imgr` is approximately `1/2` of the original size. More specifically:

  * if `Nₖ = size(img, k)` is odd, then `size(imgr, k) == (Nₖ+1) ÷ 2`.
  * if `Nₖ = size(img, k)` is even, then `size(imgr, k) == (Nₖ÷2) + 1`.

# Examples

The optional argument `dims` can be a `Tuple` or `Integer`:

```julia
A = rand(5, 5) # size: (5, 5)

restrict(A) # size: (3, 3)

restrict(A, 1) # size: (3, 5)
restrict(A, 2) # size: (5, 3)

restrict(A, (1, )) # size: (3, 5)
restrict(A, (1, 2)) # size: (3, 3)
```

Unless the input array is 1-based, the origin will be halfed:

```julia
julia> using ImageBase, OffsetArrays

julia> Ao = OffsetArray(rand(5, 4), 5, 6);

julia> Ar = restrict(Ao);

julia> axes(Ao)
(OffsetArrays.IdOffsetRange(values=6:10, indices=6:10), OffsetArrays.IdOffsetRange(values=7:10, indices=7:10))

julia> axes(Ar)
(OffsetArrays.IdOffsetRange(values=3:5, indices=3:5), OffsetArrays.IdOffsetRange(values=4:6, indices=4:6))
```

# Extended help

The term `restrict` is taken from the coarsening operation of algebraic multigrid methods; it is the adjoint of "prolongation" (which is essentially interpolation). `restrict` anti-aliases the image as it goes, so is better than a naive summation over 2x2 blocks. The implementation of `restrict` has been tuned for performance, and should be a fast method for constructing [pyramids](https://en.wikipedia.org/wiki/Pyramid_(image_processing)).

If `l` is the size of `img` along a particular dimension, `restrict` produces an array of size `(l+1)÷2` for odd `l`, and `l÷2 + 1` for even `l`. See the example below for an explanation.

See also `ImageTransformations.imresize`.

# Example

```julia
a_coarse = [0, 1, 0.3]
```

If we were to interpolate this at the halfway points, we'd get

```julia
a_fine = [0, 0.5, 1, 0.65, 0.3]
```

Note that `a_fine` is obtained from `a_coarse` via the *prolongation* operator `P` as `P*a_coarse`, where

```julia
P = [1   0   0;      # this line "copies over" the first point
     0.5 0.5 0;      # this line takes the mean of the first and second point
     0   1   0;      # copy the second point
     0   0.5 0.5;    # take the mean of the second and third
     0   0   1]      # copy the third
```

`restrict` is the adjoint of prolongation. Consequently,

```julia
julia> restrict(a_fine)
3-element Array{Float64,1}:
 0.125
 0.7875
 0.3125

julia> (P'*a_fine)/2
3-element Array{Float64,1}:
 0.125
 0.7875
 0.3125
```

where the division by 2 approximately preserves the mean intensity of the input.

As we see here, for odd-length `a_fine`, restriction is the adjoint of interpolation at half-grid points. When `length(a_fine)` is even, restriction is the adjoint of interpolation at 1/4 and 3/4-grid points. This turns out to be the origin of the `l->l÷2 + 1` behavior.

One consequence of this definition is that the edges move towards zero:

```julia
julia> restrict(ones(11))
6-element Array{Float64,1}:
 0.75
 1.0
 1.0
 1.0
 1.0
 0.75
```

In some applications (e.g., image registration), you may find it useful to trim the edges.
