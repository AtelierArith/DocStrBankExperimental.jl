```
crossbar(x, y, ymin, ymax; kwargs...)
```

クロスバーを描画します。クロスバーは、（潜在的に切り欠きのある）ボックスを持つ範囲を表します。最も一般的には `boxplot` の一部として使用されます。

## 引数

  * `x`: ボックスの位置
  * `y`: ボックス内のミッドラインの位置
  * `ymin`: ボックスの下限
  * `ymax`: ボックスの上限

## プロットタイプ

`crossbar` 関数のプロットタイプエイリアスは `CrossBar` です。

## 属性

**`color`** =  `@inherit patchcolor`  — *ドキュメントは利用できません。*

**`colormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`colorrange`** =  `automatic`  — *ドキュメントは利用できません。*

**`colorscale`** =  `identity`  — *ドキュメントは利用できません。*

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`dodge`** =  `automatic`  — *ドキュメントは利用できません。*

**`dodge_gap`** =  `0.03`  — *ドキュメントは利用できません。*

**`gap`** =  `0.2`  — 縮小係数、`width -> width * (1 - gap)`。

**`inspectable`** =  `@inherit inspectable`  — *ドキュメントは利用できません。*

**`midlinecolor`** =  `automatic`  — *ドキュメントは利用できません。*

**`midlinewidth`** =  `@inherit linewidth`  — *ドキュメントは利用できません。*

**`n_dodge`** =  `automatic`  — *ドキュメントは利用できません。*

**`notchmax`** =  `automatic`  — 切り欠きの上限。

**`notchmin`** =  `automatic`  — 切り欠きの下限。

**`notchwidth`** =  `0.5`  — 最も狭い切り欠きの幅のための `width` の乗数。

**`orientation`** =  `:vertical`  — ボックスの向き（`:vertical` または `:horizontal`）。

**`show_midline`** =  `true`  — ミッドラインを表示。

**`show_notch`** =  `false`  — 切り欠きを描画するかどうか。

**`strokecolor`** =  `@inherit patchstrokecolor`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *ドキュメントは利用できません。*

**`width`** =  `automatic`  — 縮小前のボックスの幅。
