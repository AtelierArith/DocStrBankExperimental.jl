TernaryContour

バリセントリック座標 `x`, `y`, `z` を使用して等高線プロットを描画します。すなわち、`x + y + z = 1` です。座標の重みは `w` を通じて渡されます。

## 注意事項

  * `colormap` と `color` はどちらも等高線の色に適用されます。したがって、正しい色の等高線を描画するためには、どちらか一方を `nothing` に設定する必要があります。
  * `pad_data` は、より美しい等高線を生成する目的で追加のデータポイントを加えます。これらのパッドされたポイントは、最も近い実際のデータポイントの重みの値を取ります。

## 属性

`MakieCore.Plot{TernaryDiagrams.ternarycontour}` の利用可能な属性とそのデフォルトは次のとおりです：

```
  clip_max_w  Inf
  clip_min_w  -Inf
  color       :black
  colormap    "nothing"
  levels      5
  linestyle   :solid
  linewidth   4
  pad_data    false
```
