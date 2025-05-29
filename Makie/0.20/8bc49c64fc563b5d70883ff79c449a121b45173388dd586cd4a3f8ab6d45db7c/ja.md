```
bracket(x1, y1, x2, y2; kwargs...)
bracket(x1s, y1s, x2s, y2s; kwargs...)
bracket(point1, point2; kwargs...)
bracket(vec_of_point_tuples; kwargs...)
```

各点のペア (x1, y1) と (x2, y2) の間にテキストラベルを中点に配置してブラケットを描画します。

デフォルトでは、各ラベルはブラケットポイント間の線に平行に回転します。

## 属性

`MakieCore.Plot{Makie.bracket}` の利用可能な属性とそのデフォルトは次のとおりです：

```
  align          (:center, :center)
  color          :black
  font           :regular
  fontsize       14
  justification  MakieCore.Automatic()
  linestyle      :solid
  linewidth      1.5
  offset         0
  orientation    :up
  rotation       MakieCore.Automatic()
  style          :curly
  text           ""
  textcolor      :black
  textoffset     MakieCore.Automatic()
  width          15
```
