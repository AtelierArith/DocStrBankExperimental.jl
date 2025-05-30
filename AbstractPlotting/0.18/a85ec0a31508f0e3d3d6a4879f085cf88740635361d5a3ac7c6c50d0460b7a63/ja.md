```
contourf(xs, ys, zs; kwargs...)
```

`xs`の水平グリッド位置と`ys`の垂直グリッド位置における`zs`の高さ情報の塗りつぶし等高線をプロットします。

属性`levels`は次のいずれかにすることができます。

  * n等幅のレベルまたはバンドを生成する`Int`
  * 低い方から高い方へn連続のエッジをリストする`AbstractVector{<:Real}`、これによりn-1のレベルまたはバンドが生成されます

`mode`属性を`:relative`に設定することもできます。このモードでは、`zs`の最小値と最大値の間の割合でエッジを指定します。例えば、`levels = 0.1:0.1:1.0, mode = :relative`を使用して、下位10%を除外し上位90%のバンドを描画することができます。

:normalモードでは、`-Inf`から低いエッジまでのバンドを表示したい場合、`extendlow`を`:auto`に設定すると最初のレベルと同じ色になります。または異なる色を指定することもできます（デフォルトの`nothing`は拡張バンドなしを意味します）。高いエッジから`Inf`までのバンドを表示したい場合、`extendhigh`を`:auto`に設定すると最後のレベルと同じ色になります。または異なる色を指定することもできます（デフォルトの`nothing`は拡張バンドなしを意味します）。

## 属性

`AbstractPlotting.Contourf`の利用可能な属性とそのデフォルトは次の通りです：

```
  colormap     :viridis
  extendhigh   "nothing"
  extendlow    "nothing"
  inspectable  true
  levels       10
  mode         :normal
```
