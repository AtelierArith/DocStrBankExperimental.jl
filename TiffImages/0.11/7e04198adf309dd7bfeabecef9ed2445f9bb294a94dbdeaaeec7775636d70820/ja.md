```
color(img::AbstractTIFF{ <: WidePixel}; alpha)
```

マルチスペクトル画像 `img` から色チャネルを抽出します。

オプションの `alpha` パラメータを使用すると、任意のチャネルをアルファチャネルとして使用できます。

```jldoctest; setup=:(import TiffImages: DenseTaggedImage, WidePixel; import ColorTypes: RGB, RGBA)
julia> img = DenseTaggedImage(WidePixel.([rand(RGB{Float32}) for x in 1:256, y in 1:256], [(rand(Float32),) for x in 1:256, y in 1:256]));

julia> eltype(img)
WidePixel{RGB{Float32}, Tuple{Float32}}

julia> nchannels(img)
4

julia> eltype(color(img; alpha=4)) # 4番目のチャネルをアルファチャネルとして使用
RGBA{Float32}
```
