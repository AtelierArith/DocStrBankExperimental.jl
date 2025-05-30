```
t = find_threshold(histogram, edges, UnimodalRosin())
t = find_threshold(img, UnimodalRosin(); nbins = 256)
```

ロジンのアルゴリズムを使用して、単峰分布を仮定したしきい値を生成します。

# 出力

実数 `t` を `edges` で返します。`edges` パラメータは、ヒストグラムビンに関連する区間を指定する `AbstractRange` を表します。

# 拡張ヘルプ

# 詳細

このアルゴリズムは、まずヒストグラム内で最も頻度の高いビンを選択します。次に、最大ビンの位置からヒストグラムの最後のビンまで、頻度が 0 の最初のビン（最小ビンとして知られる）を検索します。その後、最大ビンと最小ビンの両方を通る線が引かれます。線に対して最も直交距離が大きいビンがしきい値として選ばれます。

## 仮定

このアルゴリズムは以下を仮定しています：

  * ヒストグラムは単峰である。
  * 頻度が 0 のビンが常に少なくとも 1 つ存在する。存在しない場合、アルゴリズムは最後のビンを最小ビンとして使用します。

ヒストグラムに複数の頻度 0 のビンが含まれている場合、アルゴリズムは最初のゼロビンを最小として選択します。最も直交距離が大きいビンが複数ある場合、最も左のビンがしきい値として選択されます。

# 引数

関数の引数は以下でより詳細に説明されています。

## `histogram`

頻度分布を格納する `AbstractArray`。

## `edges`

頻度分布の区間がどのように分割されるかを指定する `AbstractRange`。

# 例

`TestImages` パッケージの「moonsurface」画像のしきい値を計算します。

```julia
using TestImages, ImageContrastAdjustment, HistogramThresholding

img = testimage("moonsurface")
edges, counts = build_histogram(img,256)
#=
  `counts` 配列は、インデックス 0 に最初のビンエッジ未満の頻度を格納します。
  `edges` によって区切られた区間に対してしきい値を求めているため、
  `counts` の最初のビンを破棄する必要があります。
  そうすることで、`edges` と `counts` の次元が一致します。
=#
t = find_threshold(counts[1:end], edges, UnimodalRosin())
```

# 参考文献

1. P. L. Rosin, “Unimodal thresholding,” Pattern Recognition, vol. 34, no. 11, pp. 2083–2096, Nov. 2001.[doi:10.1016/s0031-3203(00)00136-9](https://doi.org/10.1016/s0031-3203%2800%2900136-9)
