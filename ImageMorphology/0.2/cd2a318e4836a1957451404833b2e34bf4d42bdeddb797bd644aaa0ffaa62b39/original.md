```
area_opening(image, [maxtree]; min_area=64, connectivity=1) -> Array
```

Performs an *area opening* of the `image`.

*Area opening* replaces all bright components of an image that have a surface smaller than `min_area` with the darker value taken from their first ancestral component (in *max-tree* representation of `image`) that has the area no smaller than `min_area`.

# Details

Area opening is similar to morphological opening (see [`opening`](@ref)), but instead of using a fixed structuring element (e.g. disk) it employs small (less than `min_area`) components of the *max-tree*. Consequently, the `area_opening` with `min_area = 1` is the identity transformation.

In the binary case, area opening is equivalent to `remove_small_objects`; this operator is thus extended to gray-level images.

# Arguments

  * `image::GenericGrayImage`: the $N$-dimensional input image
  * `min_area::Number=64`: the smallest size (in pixels) of the image component to keep intact
  * `connectivity::Integer=1`: the neighborhood connectivity. The maximum number of orthogonal steps to reach a neighbor of the pixel. In 2D, it is 1 for a 4-neighborhood and 2 for a 8-neighborhood.
  * `maxtree::MaxTree`: optional pre-built *max-tree*. Note that `maxtree` and `connectivity` optional parameters are mutually exclusive.

# Returns

An array of the same type and shape as the `image`.

# See also

[`area_opening!`](@ref), [`area_closing`](@ref), [`diameter_opening`](@ref), [`MaxTree`](@ref), [`opening`](@ref)

# References

1. Vincent, L. (1993). *Grayscale area openings and closings, their efficient implementation and applications*, Proc. of EURASIP Workshop on Mathematical Morphology and its Applications to Signal Processing, Barcelona, Spain, 22-27
2. Soille, P. (2003). Chapter 6 *Geodesic Metrics* of *Morphological Image Analysis: Principles and Applications*, 2nd edition, Springer.

    > https://doi.org/10.1007/978-3-662-05088-0
3. Salembier, P., Oliveras, A., & Garrido, L. (1998). *Antiextensive Connected Operators for Image and Sequence Processing*. IEEE Transactions on Image Processing, 7(4), 555-570.

    > https://doi.org/10.1109/83.663500
4. Najman, L., & Couprie, M. (2006). *Building the component tree in quasi-linear time*. IEEE Transactions on Image Processing, 15(11), 3531-3539.

    > https://doi.org/10.1109/TIP.2006.877518
5. Carlinet, E., & Geraud, T. (2014). *A Comparative Review of Component Tree Computation Algorithms*. IEEE Transactions on Image Processing, 23(9), 3885-3895.

    > https://doi.org/10.1109/TIP.2014.2336551

# Examples

Creating a test image `f` (quadratic function with a maximum in the center and 4 additional local maxima):

```jldoctest; setup = :(using ImageMorphology)
julia> w = 12;

julia> f = [20 - 0.2*((x - w/2)^2 + (y-w/2)^2) for x in 0:w, y in 0:w];

julia> f[3:4, 2:6] .= 40; f[3:5, 10:12] .= 60; f[10:12, 3:5] .= 80;

julia> f[10:11, 10:12] .= 100; f[11, 11] = 100;

julia> f_aopen = area_opening(f, min_area=8, connectivity=1);
```

The peaks with a surface smaller than 8 are removed.
