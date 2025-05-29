```
imageinqrcode( code::QRCode
             , img::AbstractMatrix{Bool}
             ; rate::Real=1
             , singlemask::Bool=true
             , leftop::Tuple{Int, Int}=(-1, -1)
             , fillalignment::Bool=false
             ) where T <: Union{Bool, Nothing}
```

Plot image inside QR code.

## Arguments

  * `code::QRCode`: QR code
  * `img::AbstractMatrix{Bool}`: image to be plotted
  * `rate::Real=1`: damage rate of the error correction codewords
  * `singlemask::Bool=true`: use the default mask pattern
  * `leftop::Tuple{Int,Int}=(-1, -1)`: left top corner of the image
