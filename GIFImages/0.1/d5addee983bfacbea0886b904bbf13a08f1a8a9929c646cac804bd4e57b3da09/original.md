```
gif_encode(filepath::AbstractString, img::AbstractArray; num::Int = 64)
```

Encode the GIF colorant matrix to file. 

#### Arguments

  * `filepath` : Name of the file to which image is written.
  * `img` : 3D GIF colorant matrix which has structure of height*width*numofimags and all the images are present as slices of the 3D matrix
  * `colormapnum` : Specifies the number of colors to be used for the global colormap

### Examples

```jl
julia> using GIFImages, Downloads

julia> path = "test/data/fire.gif"
"test/data/fire.gif"

julia> img = gif_decode(path)
60×30×33 Array{RGB{N0f8},3} with eltype RGB{N0f8}

julia> gif_encode("fire.gif", img)
```
