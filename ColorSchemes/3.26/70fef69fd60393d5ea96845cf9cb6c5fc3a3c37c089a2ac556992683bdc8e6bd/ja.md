```
get(cscheme::ColorScheme, inData :: Array{Number, 2}, rangescale=:clamp)
get(cscheme::ColorScheme, inData :: Array{Number, 2}, rangescale=(minVal, maxVal))
```

2D入力データにカラースキームを適用して生成されたRGBカラーの配列を返します。

`rangescale`が`:clamp`の場合、カラースキームは0.0-1.0の範囲の値に適用され、この範囲外の値はカラースキームの端にクランプされます。

`rangescale`が`:extrema`の場合、カラースキームは`minimum(indata)..maximum(indata)`の範囲に適用されます。

それ以外の場合、`rangescale`が`:centered`の場合、カラースキームは`-maximum(abs, indata)..maximum(abs, indata)`の範囲に適用されます。

TODO: この関数はカラースキームがRGB [0.0-1.0]の値で構成されることを期待しています。より多くのカラ―タイプでも動作する必要があります。

# 例

```julia
img = get(colorschemes[:leonardo], rand(10,10)) # Juno Plotsウィンドウに表示されますが、
save("testoutput.png", img)      # これを行うにはFileIOまたは同様のものが必要です

img2 = get(colorschemes[:leonardo], 10.0 * rand(10, 10), :extrema)
img3 = get(colorschemes[:leonardo], 10.0 * rand(10, 10), (1.0, 9.0))

# PerceptualColourMapsでも動作します
using PerceptualColourMaps # 警告、PyPlot、PyCall、LaTeXStringsをインストールします
img4 = get(PerceptualColourMaps.cmap("R1"), rand(10,10))
```
