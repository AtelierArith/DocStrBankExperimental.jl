```
p = plot_image(image; height, width, zmin, zmax, darkmode, title)
```

画像行列をプロットします。

# 引数

  * `image`: (`::Matrix{Number}`) 画像行列

# キーワード

  * `width`: (`::Integer`, `=nothing`) プロットの幅
  * `height`: (`::Integer`, `=nothing`) プロットの高さ
  * `zmin`: (`::Real`, `=minimum(abs.(image[:]))`) 最小色の参照値
  * `zmax`: (`::Real`, `=maximum(abs.(image[:]))`) 最大色の参照値
  * `darkmode`: (`::Bool`, `=false`) ダークモードスタイルを表示するかどうかを示すブール値
  * `title`: (`::String`, `=""`) プロットのタイトル

# 戻り値

  * `p`: (`::PlotlyJS.SyncPlot`) 画像行列のプロット
