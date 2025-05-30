```
boxplot(x, y; kwargs...)
```

Tukeyスタイルのボックスプロットを描画します。ボックスプロットには3つのコンポーネントがあります：

  * 中央値を示すミッドラインを持つ四分位範囲（IQR）を跨ぐ`crossbar`
  * `range * iqr`を跨ぐ`errorbar`のひげ
  * ひげの外側にあるデータ、すなわち外れ値を示すポイント

## 引数

  * `x`: カテゴリの位置
  * `y`: ボックス内の変数

## プロットタイプ

`boxplot`関数のプロットタイプエイリアスは`BoxPlot`です。

## 属性

**`color`** =  `@inherit patchcolor`  — *ドキュメントは利用できません。*

**`colormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`colorrange`** =  `automatic`  — *ドキュメントは利用できません。*

**`colorscale`** =  `identity`  — *ドキュメントは利用できません。*

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`dodge`** =  `automatic`  — 同じ`x`位置に複数の並んだボックスを作成するためのグループ化変数の整数のベクター（データの長さ）。

**`dodge_gap`** =  `0.03`  — ドッジされたボックス間の間隔。

**`gap`** =  `0.2`  — 縮小係数、`width -> width * (1 - gap)`。

**`inspectable`** =  `@inherit inspectable`  — *ドキュメントは利用できません。*

**`marker`** =  `@inherit marker`  — *ドキュメントは利用できません。*

**`markersize`** =  `@inherit markersize`  — *ドキュメントは利用できません。*

**`mediancolor`** =  `@inherit linecolor`  — *ドキュメントは利用できません。*

**`medianlinewidth`** =  `@inherit linewidth`  — *ドキュメントは利用できません。*

**`n_dodge`** =  `automatic`  — *ドキュメントは利用できません。*

**`notchwidth`** =  `0.5`  — ノッチの最狭幅のための`width`の乗数。

**`orientation`** =  `:vertical`  — ボックスの向き（`:vertical`または`:horizontal`）。

**`outliercolor`** =  `automatic`  — *ドキュメントは利用できません。*

**`outlierstrokecolor`** =  `@inherit markerstrokecolor`  — *ドキュメントは利用できません。*

**`outlierstrokewidth`** =  `@inherit markerstrokewidth`  — *ドキュメントは利用できません。*

**`range`** =  `1.5`  — ひげの長さを制御するIQRの倍数。

**`show_median`** =  `true`  — 中央値をミッドラインとして表示。

**`show_notch`** =  `false`  — ノッチを描画。

**`show_outliers`** =  `true`  — 外れ値をポイントとして表示。

**`strokecolor`** =  `@inherit patchstrokecolor`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *ドキュメントは利用できません。*

**`weights`** =  `automatic`  — 統計的重みのベクター（データの長さ）。デフォルトでは、各観測値の重みは`1`です。

**`whiskercolor`** =  `@inherit linecolor`  — *ドキュメントは利用できません。*

**`whiskerlinewidth`** =  `@inherit linewidth`  — *ドキュメントは利用できません。*

**`whiskerwidth`** =  `0.0`  — ひげのTの幅のための`width`の乗数、または`width`に合わせるための`:match`。

**`width`** =  `automatic`  — 縮小前のボックスの幅。
