```
hexbin(xs, ys; kwargs...)
```

観測値 `xs` と `ys` のための六角形ビンを持つヒートマップをプロットします。

## プロットタイプ

`hexbin` 関数のプロットタイプエイリアスは `Hexbin` です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。`plot(alpha=0.2, color=(:red, 0.5)` のように複数のアルファは掛け算されます。

**`bins`** =  `20`  — `Int` の場合、x および y 方向のビンの数を設定します。`NTuple{2, Int}` の場合、x と y のビンの数を別々に設定します。

**`cellsize`** =  `nothing`  — `Real` の場合、幅 `cellsize` の等辺六角形を作成します。`Tuple{Real, Real}` の場合、六角形の幅と高さを別々に指定します。

**`colormap`** =  `@inherit colormap :viridis`  — 数値 `color` のためにサンプリングされるカラーマップを設定します。`PlotUtils.cgrad(...)`、`Makie.Reverse(any_colormap)` も使用できますし、ColorBrewer や PlotUtils の任意のシンボルも使用できます。利用可能なすべてのカラ―グラデーションを確認するには、`Makie.available_gradients()` を呼び出すことができます。

**`colorrange`** =  `automatic`  — `colormap` の開始点と終了点を表す値。

**`colorscale`** =  `identity`  — 色変換関数。任意の関数を使用できますが、`Colorbar` と一緒に `identity`、`log`、`log2`、`log10`、`sqrt`、`logit`、`Makie.pseudolog10` および `Makie.Symlog10` と一緒にうまく機能します。

**`highclip`** =  `automatic`  — カラーレンジを超える任意の値の色。

**`lowclip`** =  `automatic`  — カラーレンジ未満の任意の値の色。

**`nan_color`** =  `:transparent`  — NaN 値の色。

**`strokecolor`** =  `:black`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `0`  — *ドキュメントは利用できません。*

**`threshold`** =  `1`  — 表示されるビン内の最小観測数。0 の場合、データ制限に収まるすべてのゼロカウントの六角形が表示されます。

**`weights`** =  `nothing`  — 各観測値の重み。`nothing`（各観測値は重み 1 を持つ）または任意の `AbstractVector{<: Real}` または `StatsBase.AbstractWeights` であることができます。 ```
