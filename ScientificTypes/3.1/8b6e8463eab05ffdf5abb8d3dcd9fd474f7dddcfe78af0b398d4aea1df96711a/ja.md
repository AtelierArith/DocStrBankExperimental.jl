```
coerce(image::AbstractArray{<:Real, N}, I)
```

配列 `image` が1つ以上の画像を表す場合、データの変換されたバージョンを返し、適切な科学的解釈 `I` を強制します：

| 単一またはコレクション？ |                   N |            I |                  結果の `scitype` |
| ------------:| -------------------:| ------------:| ------------------------------:|
|           単一 |                   2 |  `GrayImage` |               `GrayImage{W,H}` |
|           単一 |                   3 | `ColorImage` |              `ColorImage{W,H}` |
|       コレクション |                   3 |  `GrayImage` |  `AbstractVector{<:GrayImage}` |
|       コレクション | 4 (W x H x {1} x C) |  `GrayImage` |  `AbstractVector{<:GrayImage}` |
|       コレクション |                   4 | `ColorImage` | `AbstractVector{<:ColorImage}` |

```
imgs = rand(10, 10, 3, 5)
v = coerce(imgs, ColorImage)

julia> typeof(v)
Vector{Matrix{ColorTypes.RGB{Float64}}}

julia> scitype(v)
AbstractVector{ColorImage{10, 10}}

```
