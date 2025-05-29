```
    NonmaximaSuppression <: AbstractEdgeThinningAlgorithm
    NonmaximaSuppression(; threshold::Union{Number, Percentile} = Percentile(20))

    f = NonmaximaSuppression()
    f(out::AbstractArray, mag::AbstractArray, g₁::AbstractArray, g₂::AbstractArray, f::NonmaximaSuppression)
```

Isolates local maxima of gradient magnitude `mag` along the local gradient direction and stores the result in `out`.  The arguments `g₁` and `g₂` represent the  gradient in the first spatial dimension (y), and the second spatial dimension (x), respectively.

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
# Instantiate the NonmaximaSuppression functor.
f = NonmaximaSuppression()

# Suppress the non-maximal gradient magnitudes and store the result in `nms`.
f(nms, mag, g₁, g₂)

imshow(img)
imshow(mag)
imshow(nms)
```

# References

J. Canny, "A Computational Approach to Edge Detection," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. PAMI-8, no. 6, pp. 679-698, Nov. 1986, doi: 10.1109/TPAMI.1986.4767851.
