```
plot_genealogy(genealogy[, ω]; kwargs...)
```

系譜をプロットします。

`ω` に祖先のエッジと頂点のみがプロットされます。

これは `Moonshine.jl` への拡張として実装されています。このメソッドを使用するには、[`GraphMakie`](@ref) をインポートする必要があります（および [Makie](https://github.com/MakieOrg/Makie.jl) バックエンド）。

さらに [`plot_layout`](@ref) も参照してください。

# 引数

  * `wild_color` (`:blue`): `ω` において野生マーカーのみを持つ野生頂点の色。
  * `derived_color` (`:red`): 派生（非野生）頂点の色。
  * `arrow_show` (`false`): 矢印を描画するかどうか。
  * `edge_color` (`:gray`): エッジの色。
  * `edge_width` (`3`): エッジの幅。
  * `layout` (`plot_layout(genealogy)`): レイアウト関数。
  * `attributes...`: [`GraphMakie.graphplot`](@extref) に直接渡される属性。
