```
t = find_threshold(histogram, edges, Intermodes(maxiter=8000))
t = find_threshold(img, Intermodes(); nbins = 256)
```

ヒストグラムが二峰性であると仮定した場合、ヒストグラムは長さ3の平均フィルタを使用して平滑化され、2つのモードが残るまで処理されます。しきい値は2つのモードの平均値に設定されます。

# 出力

実数 `t` を `edges` に返します。`edges` パラメータは、ヒストグラムビンに関連する区間を指定する `AbstractRange` を表します。

# 拡張ヘルプ

# 詳細

`maxiter` 回の反復後も平滑化されたヒストグラムが二峰性でない場合、アルゴリズムはしきい値を選択するために `UnimodalRosin` メソッドにフォールバックします。

# 引数

関数の引数は以下でより詳細に説明されています。

## `histogram`

頻度分布を格納する `AbstractArray`。

## `edges`

頻度分布の区間がどのように分割されるかを指定する `AbstractRange`。

## `maxiter`

最大平滑化反復回数を指定する `Int`。指定しない場合はデフォルト値の1000が使用されます。

# 例

`TestImages` パッケージの「カメラマン」画像のしきい値を計算します。

```julia

using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("cameraman")
edges, counts = build_histogram(img,256)
#=
  `counts` 配列はインデックス0に最初のビンエッジよりも低い頻度を格納します。
  `edges` によって区切られた区間でしきい値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  そうすることで `edges` と `counts` の次元が一致します。
=#
t = find_threshold(counts[1:end], edges, Intermodes())
```

# 参考文献

1. C. A. Glasbey, “An Analysis of Histogram-Based Thresholding Algorithms,” CVGIP: Graphical Models and Image Processing, vol. 55, no. 6, pp. 532–537, Nov. 1993. [doi:10.1006/cgip.1993.1040](https://doi.org/10.1006/cgip.1993.1040)
