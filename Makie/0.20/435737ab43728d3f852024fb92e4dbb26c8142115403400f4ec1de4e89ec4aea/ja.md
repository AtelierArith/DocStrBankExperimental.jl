```
stairs(xs, ys; kwargs...)
```

階段関数をプロットします。

`step` パラメータは以下の値を取ることができます：

  * `:pre`: ステップの水平部分は `xs` の各値の左側に延びます。
  * `:post`: ステップの水平部分は `xs` の各値の右側に延びます。
  * `:center`: ステップの水平部分は `xs` の隣接する2つの値の間の中間に延びます。

stemの変換特性は `PointBased` です。

## 属性

`MakieCore.Plot{Makie.stairs}` の利用可能な属性とそのデフォルトは次の通りです：

```
  alpha           1.0
  color           :black
  colormap        :viridis
  colorrange      MakieCore.Automatic()
  colorscale      identity
  cycle           [:color]
  depth_shift     0.0f0
  highclip        MakieCore.Automatic()
  inspectable     true
  linestyle       "nothing"
  linewidth       1.5
  lowclip         MakieCore.Automatic()
  nan_color       :transparent
  overdraw        false
  space           :data
  ssao            false
  step            :pre
  transparency    false
  visible         true
```
