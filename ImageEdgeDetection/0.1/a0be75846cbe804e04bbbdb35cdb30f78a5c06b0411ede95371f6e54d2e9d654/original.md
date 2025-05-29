```
    SubpixelNonmaximaSuppression <: AbstractEdgeThinningAlgorithm
    SubpixelNonmaximaSuppression(; threshold::Union{Number, Percentile} = Percentile(20))

    f = SubpixelNonmaximaSuppression()
    f(out₁::AbstractArray, out₂::Matrix{<:AbstractArray}, mag::AbstractArray, g₁::AbstractArray, g₂::AbstractArray, f::SubpixelNonmaximaSuppression)
```

Isolates local maxima of gradient magnitude `mag` along the local gradient direction to subpixel precision.  The arguments `g₁` and `g₂` represent the gradient in the first spatial dimension (y), and the second spatial dimension (x), respectively.

The integer components of the local maxima correspond to non-zero row and column entries `out₁`. The accompanying subpixel offsets  are stored in a 2-D array `out₂` as length-2 vectors. One can recover the  subpixel coordinates by adding the subpixel offsets to the integer components.

# Details

TODO

# Example

```julia

using TestImages, FileIO, ImageView, ImageEdgeDetection, ImageFiltering

img =  testimage("mandril_gray")

# Gradient in the first and second spatial dimension
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# Gradient magnitude
mag = hypot.(g₁, g₂)

nms = zeros(eltype(mag), axes(mag))
subpixel_offsets = zeros(SVector{2,Float64}, axes(mag))

# Instantiate the NonmaximaSuppression functor.
f = SubpixelNonmaximaSuppression()

# Suppress the non-maximal gradient magnitudes and store the result in `nms`.
f(nms, subpixel_offsets, mag, g₁, g₂)

imshow(img)
imshow(mag)
imshow(nms)
```

# References

1. J. Canny, "A Computational Approach to Edge Detection," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. PAMI-8, no. 6, pp. 679-698, Nov. 1986, doi: 10.1109/TPAMI.1986.4767851.
2. F. Devernay, "A non-maxima suppression method for edge detection with sub-pixel accuracy", Tech. Report RR-2724, INRIA, 1995.
