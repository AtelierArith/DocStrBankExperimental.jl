```
density(values)
```

`values`のカーネル密度推定をプロットします。

## プロットタイプ

`density`関数のプロットタイプエイリアスは`Density`です。

## 属性

**`alpha`** =  `1.0`  — カラーマップまたは色属性のアルファ値。plot(alpha=0.2, color=(:red, 0.5)のように複数のアルファがある場合は、乗算されます。

**`bandwidth`** =  `automatic`  — カーネル密度のバンド幅。`automatic`の場合は自動的に決定されます。

**`boundary`** =  `automatic`  — 密度推定の境界。`automatic`の場合は自動的に決定されます。

**`color`** =  `@inherit patchcolor`  — 通常は単一の色に設定されますが、グラデーションで色付けするために`:x`または`:y`に設定することもできます。`direction = :x`のときに`:y`を使用する場合（またはその逆）、2要素のカラーマップのみが正しく機能することに注意してください。

**`colormap`** =  `@inherit colormap`  — *ドキュメントは利用できません。*

**`colorrange`** =  `Makie.automatic`  — *ドキュメントは利用できません。*

**`colorscale`** =  `identity`  — *ドキュメントは利用できません。*

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`direction`** =  `:x`  — `values`が分布する次元。`:x`または`:y`にできます。

**`inspectable`** =  `@inherit inspectable`  — *ドキュメントは利用できません。*

**`linestyle`** =  `nothing`  — *ドキュメントは利用できません。*

**`npoints`** =  `200`  — `direction`で設定された次元に沿った推定曲線の解像度。

**`offset`** =  `0.0`  — 複数の密度を重ねるために密度のベースラインをシフトします。

**`strokearound`** =  `false`  — *ドキュメントは利用できません。*

**`strokecolor`** =  `@inherit patchstrokecolor`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *ドキュメントは利用できません。*

**`weights`** =  `automatic`  — `values`に統計的重みのベクトルを割り当てます。
