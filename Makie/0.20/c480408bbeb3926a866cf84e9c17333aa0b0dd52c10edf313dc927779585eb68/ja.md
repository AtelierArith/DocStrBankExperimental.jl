```
contourf(xs, ys, zs; kwargs...)
```

`xs`の水平グリッド位置と`ys`の垂直グリッド位置における`zs`の高さ情報の塗りつぶし等高線をプロットします。

属性`levels`は次のいずれかにすることができます。

  * n等幅のレベルまたはバンドを生成する`Int`
  * 低から高までのn連続エッジをリストする`AbstractVector{<:Real}`で、これによりn-1のレベルまたはバンドが生成されます

`mode`属性を`:relative`に設定することもできます。このモードでは、`zs`の最小値と最大値の間の割合でエッジを指定します。例えば、`levels = 0.1:0.1:1.0, mode = :relative`を使用して、下位10%を除外し上位90%のバンドを描画することができます。

:normalモードでは、`-Inf`から低エッジまでのバンドを表示したい場合、`extendlow`を`:auto`に設定すると最初のレベルと同じ色になります。または異なる色を指定することもできます（デフォルトの`nothing`は拡張バンドなしを意味します）。高エッジから`Inf`までのバンドを表示したい場合、`extendhigh`を`:auto`に設定すると最後のレベルと同じ色になります。または異なる色を指定することもできます（デフォルトの`nothing`は拡張バンドなしを意味します）。

`levels`が`Int`の場合、すべての`zs`がカバーされるため、等高線プロットは長方形になります。これが、`Axis`がそのようなcontourfプロットのためにタイトな制限をデフォルトにしている理由です。しかし、`levels`を`AbstractVector{<:Real}`として指定した場合、等高線プロットが不規則な形状を持つ可能性があるため、軸の制限にはデフォルトのマージンが含まれることに注意してください。`tightlimits!(ax)`を使用して、`Int`の動作に似た制限を厳しくすることができます。

## 属性

`MakieCore.Plot{Makie.contourf}`の利用可能な属性とそのデフォルトは次のとおりです：

```
  colormap      :viridis
  colorscale    identity
  extendhigh    "nothing"
  extendlow     "nothing"
  inspectable   true
  levels        10
  mode          :normal
  nan_color     :transparent
  transparency  false
```
