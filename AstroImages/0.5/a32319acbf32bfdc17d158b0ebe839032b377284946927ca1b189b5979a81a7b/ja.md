```
composecolors(
    images,
    cmap=["#F00", "#0F0", "#00F"];
    clims,
    stretch,
    contrast,
    bias,
    multiplier
)
```

複数の画像のカラー合成を作成するには、`imview`を適用し、結果をブレンドします。この関数は、任意の数のチャンネル（例：赤、緑、青、そして水素アルファ）を使用してRGB合成を作成するために使用でき、2つの異なるカラーマップを使用してラジオデータと光学データをブレンドするようなよりエキゾチックな画像にも使用できます。

`cmap`は、色素、名前付き色（Colors.jlを参照）、またはカラースキーム（ColorSchemes.jlを参照）のリストである必要があります。`clims`、`stretch`、`contrast`、および`bias`は`imview`に渡されます。これらは単一の値または各画像の異なる値のリストであることができます。

返される画像のヘッダーは最初の画像からコピーされます。

例：

```julia
# 基本的なRGB
composecolors([redimage, greenimage, blueimage])
# ブレンドの前に非線形ストレッチ
composecolors([redimage, greenimage, blueimage], stretch=asinhstretch)
# 3つ以上のチャンネルが許可されます（ピンクのHアルファ）
composecolors(
    [antred, antgreen, antblue, anthalp],
    ["red", "green", "blue", "maroon1"],
    multiplier=[1,2,1,1]
)
# 混合可能
composecolors([radioimage, xrayimage], [:ice, :magma], clims=extrema)
composecolors([radioimage, xrayimage], [:magma, :viridis], clims=[Percent(99), Zscale()])
```
