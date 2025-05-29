Quantize phase values in an image.

```
Usage:  qimg = quantizephase(img, N)

Arguments: img::Array{T,2} where T <: Real - Image to be processed
                     N::Integer - Desired number of quantized phase values

Returns:  qimg::Array{Float64,2} - Phase quantized image
```

Phase values in an image are important.  However, despite this, they can be quantized very heavily with little perceptual loss.  The value of N can be as low as 4, or even 3!  Using N = 2 is also worth a look.

See also: [`swapphase`](@ref)
