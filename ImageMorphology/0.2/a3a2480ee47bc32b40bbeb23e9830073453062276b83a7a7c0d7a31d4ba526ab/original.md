```
diameter_closing(image, [maxtree]; min_diameter=8, connectivity=1) -> Array
```

Performs a *diameter closing* of the `image`.

*Diameter closing* replaces all dark structures of an image that have the diameter (the widest dimension of their bounding box) smaller than `min_diameter` with the brighter value taken from their first ancestral component (in *max-tree* representation of `image`) that has the diameter no smaller than `min_diameter`.

# Arguments

  * `image::GenericGrayImage`: the $N$-dimensional input image
  * `min_diameter::Number=8`: the minimal length (in pixels) of the widest dimension of the bounding box of the image component to keep intact
  * `connectivity::Integer=1`: the neighborhood connectivity. The maximum number of orthogonal steps to reach a neighbor of the pixel. In 2D, it is 1 for a 4-neighborhood and 2 for a 8-neighborhood.
  * `maxtree::MaxTree`: optional pre-built *max-tree*. Note that `maxtree` and `connectivity` optional parameters are mutually exclusive.

# Returns

An array of the same type and shape as the `image`.

# See also

[`diameter_closing!`](@ref), [`diameter_opening`](@ref), [`area_closing`](@ref), [`MaxTree`](@ref), [`closing`](@ref)

# References

1. Walter, T., & Klein, J.-C. (2002). *Automatic Detection of Microaneurysms in Color Fundus Images of the Human Retina by Means of the Bounding Box Closing*. In A. Colosimo, P. Sirabella, A. Giuliani (Eds.), *Medical Data Analysis. Lecture Notes in Computer Science*, vol 2526, 210-220. Springer Berlin Heidelberg.

    > https://doi.org/10.1007/3-540-36104-9_23
2. Carlinet, E., & Geraud, T. (2014). *A Comparative Review of Component Tree Computation Algorithms*. IEEE Transactions on Image Processing, 23(9), 3885-3895.

    > https://doi.org/10.1109/TIP.2014.2336551

# Examples

Creating a test image `f` (quadratic function with a minimum in the center and 4 additional local minima):

```jldoctest; setup = :(using ImageMorphology)
julia> w = 12;

julia> f = [180 + 0.2*((x - w/2)^2 + (y-w/2)^2) for x in 0:w, y in 0:w];

julia> f[3:4, 2:6] .= 40; f[3:5, 10:12] .= 60; f[10:12, 3:5] .= 80;

julia> f[10:11, 10:12] .= 100; f[11, 11] = 100;

julia> f_dclose = diameter_closing(f, min_diameter=3, connectivity=1);
```

All small minima with a diameter of 2 or less are removed. For the remaining minima the widest bounding box side is at least 3.
