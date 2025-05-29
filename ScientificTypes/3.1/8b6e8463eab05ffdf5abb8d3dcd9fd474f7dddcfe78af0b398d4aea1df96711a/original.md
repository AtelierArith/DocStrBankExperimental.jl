```
coerce(image::AbstractArray{<:Real, N}, I)
```

Given an array called `image` representing one or more images, return a transformed version of the data so as to enforce an appropriate scientific interpretation `I`:

| single or collection ? |                   N |            I |            `scitype` of result |
| ----------------------:| -------------------:| ------------:| ------------------------------:|
|                 single |                   2 |  `GrayImage` |               `GrayImage{W,H}` |
|                 single |                   3 | `ColorImage` |              `ColorImage{W,H}` |
|             collection |                   3 |  `GrayImage` |  `AbstractVector{<:GrayImage}` |
|             collection | 4 (W x H x {1} x C) |  `GrayImage` |  `AbstractVector{<:GrayImage}` |
|             collection |                   4 | `ColorImage` | `AbstractVector{<:ColorImage}` |

```
imgs = rand(10, 10, 3, 5)
v = coerce(imgs, ColorImage)

julia> typeof(v)
Vector{Matrix{ColorTypes.RGB{Float64}}}

julia> scitype(v)
AbstractVector{ColorImage{10, 10}}

```
