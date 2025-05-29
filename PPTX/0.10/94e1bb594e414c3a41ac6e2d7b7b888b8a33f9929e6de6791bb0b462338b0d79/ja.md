```julia
Picture(source::String; top::Int=0, left::Int=0, size::Int = 40)
```

  * `source::String` 画像ファイルのパス
  * `top::Int` 上からのmm
  * `left::Int` 左からのmm

内部的にサイズはEMUに変換されます。

# 例

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

オプションで、FileIOによってサポートされていないファイルタイプ（SVGなど）のために、`size_x` と `size_y` を手動で設定できます。

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
