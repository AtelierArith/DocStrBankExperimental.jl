```
restrict(img[, region]) -> imgr
```

Reduce the size of `img` by approximately two-fold along the dimensions listed in `region`, or all spatial coordinates if `region` is not specified. The term `restrict` is taken from the coarsening operation of algebraic multigrid methods; it is the adjoint of "prolongation" (which is essentially interpolation). `restrict` anti-aliases the image as it goes, so is better than a naive summation over 2x2 blocks. The implementation of `restrict` has been tuned for performance, and should be a fast method for constructing [pyramids](https://en.wikipedia.org/wiki/Pyramid_(image_processing)).

If `l` is the size of `img` along a particular dimension, `restrict` produces an array of size `(l+1)÷2` for odd `l`, and `l÷2 + 1` for even `l`. See the example below for an explanation.

See also [`imresize`](@ref).

# Example

```julia
a_course = [0, 1, 0.3]
```

If we were to interpolate this at the halfway points, we'd get

```julia
a_fine = [0, 0.5, 1, 0.65, 0.3]
```

Note that `a_fine` is obtained from `a_course` via the *prolongation* operator `P` as `P*a_course`, where

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
