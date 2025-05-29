```julia
Picture(source::String; top::Int=0, left::Int=0, size::Int = 40)
```

  * `source::String` path of image file
  * `top::Int` mm from the top
  * `left::Int` mm from the left

Internally the sizes are converted EMUs.

# Examples

```julia
julia> using PPTX

julia> img = Picture(joinpath(PPTX.ASSETS_DIR, "cauliflower.jpg"))
Picture
 source is "./cauliflower.jpg"
 offset_x is 0 EMUs
 offset_y is 0 EMUs
 size_x is 1440000 EMUs
 size_y is 1475072 EMUs

```

Optionally, you can set the `size_x` and `size_y` manually for filetypes not supported by FileIO, such as SVG.

```julia
julia> using PPTX

julia> img = Picture(joinpath(PPTX.ASSETS_DIR, "julia_logo.svg"); size_x=40, size_y=30)
Picture
 source is "./julia_logo.svg"
 offset_x is 0 EMUs
 offset_y is 0 EMUs
 size_x is 1440000 EMUs
 size_y is 1080000 EMUs

```
