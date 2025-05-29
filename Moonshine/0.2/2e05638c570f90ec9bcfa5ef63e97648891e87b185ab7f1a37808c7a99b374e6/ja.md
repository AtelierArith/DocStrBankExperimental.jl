```julia
plot_sequence(h; nbins, height, kwargs...)

```

ハプロタイプのUnicodeグラフィック表現。

# 引数

  * `nbins` (`clamp(length(h), 1, 69)`): ビンの数
  * ̀`height` (`7`): 行の数
  * `kwargs`: `UnicodePlots.heatmap`に直接渡される引数
