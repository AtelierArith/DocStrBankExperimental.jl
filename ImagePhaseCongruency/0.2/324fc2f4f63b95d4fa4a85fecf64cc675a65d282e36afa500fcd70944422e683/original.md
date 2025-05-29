Demonstrates phase - amplitude swapping between images.

```
Usage:   (newimg1, newimg2) = swapphase(img1, img2)

Arguments:
 img1, img2::Array{<:Real,2} - Two images of same size to be used as input

Returns:
    newimg1::Array{Float64,2} - Image obtained from the phase of img1
                                and the magnitude of img2.
    newimg2::Array{Float64,2} - Phase of img2, magnitude of img1.
```

See also: [`quantizephase`](@ref), [`nophase`](@ref)
