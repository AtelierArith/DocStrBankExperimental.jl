```
gif_encode(filepath::AbstractString, img::AbstractArray; num::Int = 64)
```

GIFカラーマトリックスをファイルにエンコードします。

#### 引数

  * `filepath` : 画像が書き込まれるファイルの名前。
  * `img` : 高さ*幅*画像数の構造を持つ3D GIFカラーマトリックスで、すべての画像が3Dマトリックスのスライスとして存在します。
  * `colormapnum` : グローバルカラーマップに使用される色の数を指定します。

### 例

```jl
julia> using GIFImages, Downloads

julia> path = "test/data/fire.gif"
"test/data/fire.gif"

julia> img = gif_decode(path)
60×30×33 Array{RGB{N0f8},3} with eltype RGB{N0f8}

julia> gif_encode("fire.gif", img)
```
