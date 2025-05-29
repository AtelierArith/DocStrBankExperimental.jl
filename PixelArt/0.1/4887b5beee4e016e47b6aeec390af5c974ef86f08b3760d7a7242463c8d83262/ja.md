```
pixel(img, [, n_color, w, h]) -> Array{RGB{Float64}}
```

# 例

```jldoctest
julia> using PixelArt

julia> using Images

julia> img = load("img.jpg");

julia> img_pixel = pixel(img);

julia> save("img_pixel.jpg", img_pixel)
```
