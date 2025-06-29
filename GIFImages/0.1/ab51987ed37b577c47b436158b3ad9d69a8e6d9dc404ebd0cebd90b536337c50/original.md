```
gif_decode(filepath::AbstractString; use_localpalette=false)
```

Decode the GIF image as colorant matrix. The source data needs to be a filename.

#### Arguments

  * `filepath::AbstractString` : Path to the gif file
  * `use_localpalette::Bool=false` : While decoding, using this argument use of local colormap or global colormap for a particular slice can be specified. Gif files are palette based and have a global colormap(max `256 colors`) but slices/images in gif can have their own local colormap specific to a particular slice/image.

#### Examples

```jl julia> using GIFImages, Downloads

julia> path = "test/data/fire.gif" "test/data/fire.gif"

julia> img = gif_decode(path) 60×30×33 Array{RGB{N0f8},3} with eltype RGB{N0f8}
