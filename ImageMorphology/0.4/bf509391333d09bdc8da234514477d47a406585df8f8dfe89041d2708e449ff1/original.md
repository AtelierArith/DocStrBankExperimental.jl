```
local_maxima(image, [maxtree]; connectivity=1) -> Array
```

Determines and labels all *local maxima* of the `image`.

# Details

The *local maximum* is defined as the connected set of pixels that have the same value, which is greater than the values of all pixels in direct neighborhood of the set.

Technically, the implementation is based on the *max-tree* representation of an image. It's beneficial if the max-tree is already computed, otherwise `ImageFiltering.findlocalmaxima` would be more efficient.

# Arguments

  * `image::GenericGrayImage`: the $N$-dimensional input image
  * `connectivity::Integer=1`: the neighborhood connectivity. The maximum number of orthogonal steps to reach a neighbor of the pixel. In 2D, it is 1 for a 4-neighborhood and 2 for a 8-neighborhood.
  * `maxtree::MaxTree`: optional pre-built *max-tree*. Note that `maxtree` and `connectivity` optional parameters are mutually exclusive.

# Returns

An integer array of the same shape as the `image`. Pixels that are not local maxima have 0 value. Pixels of the same local maximum share the same positive value (the local maximum id).

# See also

[`MaxTree`](@ref), [`local_maxima!`](@ref), [`local_minima`](@ref), `ImageFiltering.findlocalmaxima`

# Examples

Create `f` (quadratic function with a maximum in the center and 4 additional constant maxima):

```jldoctest; setup = :(using ImageMorphology)
julia> w = 10;

julia> f = [20 - 0.2*((x - w/2)^2 + (y-w/2)^2) for x in 0:w, y in 0:w];

julia> f[3:5, 3:5] .= 40; f[3:5, 8:10] .= 60; f[8:10, 3:5] .= 80; f[8:10, 8:10] .= 100;

julia> f_maxima = local_maxima(f); # Get all local maxima of `f`
```

The resulting image contains the 4 labeled local maxima.
