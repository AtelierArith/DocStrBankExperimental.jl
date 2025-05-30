```
color(img::AbstractTIFF{ <: WidePixel}; alpha)
```

マルチスペクトル画像 `img` からカラーチャンネルを抽出します。

オプションの `alpha` パラメータを使用すると、任意のチャンネルをアルファチャンネルとして使用できます。

```jldoctest; setup=:(import TiffImages: DenseTaggedImage, WidePixel; import ColorTypes: RGB, RGBA)
julia> img = DenseTaggedImage(WidePixel.([rand(RGB{Float32}) for x in 1:256, y in 1:256], [(rand(Float32),) for x in 1:256, y in 1:256]));

julia> eltype(img)
WidePixel{RGB{Float32}, Tuple{Float32}}

julia> nchannels(img)
4

julia> eltype(color(img; alpha=4)) # 4番目のチャンネルをアルファチャンネルとして使用
RGBA{Float32}
```
