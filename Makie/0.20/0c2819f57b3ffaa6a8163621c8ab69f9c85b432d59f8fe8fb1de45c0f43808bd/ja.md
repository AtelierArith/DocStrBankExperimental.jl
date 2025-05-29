```
waterfall(x, y; kwargs...)
```

個々の正の要素と負の要素を視覚化し、合計結果を隣接するスタックバーの棒グラフとして表示するための[ウォーターフォールチャート](https://en.wikipedia.org/wiki/Waterfall_chart)をプロットします。

## 属性

`MakieCore.Plot{Makie.waterfall}`の利用可能な属性とそのデフォルトは次のとおりです：

```
  cycle            [:color => :patchcolor]
  direction_color  :white
  dodge            MakieCore.Automatic()
  dodge_gap        0.03
  final_color      RGBA{Float64}(0.8980392156862745,0.8980392156862745,0.8980392156862745,0.5)
  final_dodge_gap  0
  final_gap        MakieCore.Automatic()
  gap              0.2
  marker_neg       :dtriangle
  marker_pos       :utriangle
  n_dodge          MakieCore.Automatic()
  show_direction   false
  show_final       false
  stack            MakieCore.Automatic()
  width            MakieCore.Automatic()
```

さらに、`barplot`と同じ属性がサポートされています。
