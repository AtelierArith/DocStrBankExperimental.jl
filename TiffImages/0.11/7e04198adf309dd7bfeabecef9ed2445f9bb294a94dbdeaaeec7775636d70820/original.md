```
color(img::AbstractTIFF{ <: WidePixel}; alpha)
```

Extract the color channels from multispectral image `img`

The optional `alpha` parameter allows an arbitrary channel to be used as the alpha channel

```jldoctest; setup=:(import TiffImages: DenseTaggedImage, WidePixel; import ColorTypes: RGB, RGBA)
julia> img = DenseTaggedImage(WidePixel.([rand(RGB{Float32}) for x in 1:256, y in 1:256], [(rand(Float32),) for x in 1:256, y in 1:256]));

julia> eltype(img)
WidePixel{RGB{Float32}, Tuple{Float32}}

julia> nchannels(img)
4

julia> eltype(color(img; alpha=4)) # use the fourth channel as an alpha channel
RGBA{Float32}
```
