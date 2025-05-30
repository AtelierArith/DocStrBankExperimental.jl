```
hist(values)
```

`values`のヒストグラムをプロットします。

## プロットタイプ

`hist`関数のプロットタイプエイリアスは`Hist`です。

## 属性

**`bar_labels`** =  `nothing`  — *ドキュメントは利用できません。*

**`bins`** =  `15`  — `values`の範囲にわたってその数の等幅ビンを作成するための`Int`であることができます。あるいは、ビンのエッジのソートされた反復可能なオブジェクトであることもできます。

**`color`** =  `@inherit patchcolor`  — 色は次のいずれかであることができます：

  * `bins`の色のベクトル
  * 単一の色
  * `:values`、ヒストグラムの値でバーに色を付けるため

**`cycle`** =  `[:color => :patchcolor]`  — *ドキュメントは利用できません。*

**`direction`** =  `:y`  — バーの方向を設定します。

**`fillto`** =  `automatic`  — バーが開始する位置を定義します。

**`flip_labels_at`** =  `Inf`  — *ドキュメントは利用できません。*

**`gap`** =  `0`  — バー間の隙間（barplotを参照）。

**`label_color`** =  `@inherit textcolor`  — *ドキュメントは利用できません。*

**`label_font`** =  `@inherit font`  — *ドキュメントは利用できません。*

**`label_formatter`** =  `bar_label_formatter`  — *ドキュメントは利用できません。*

**`label_offset`** =  `5`  — *ドキュメントは利用できません。*

**`label_size`** =  `20`  — *ドキュメントは利用できません。*

**`normalization`** =  `:none`  — ヒストグラムを正規化することを許可します。可能な値は：

  * `:pdf`: 重みとビンサイズの合計で正規化します。結果として得られるヒストグラムはノルム1を持ち、PDFを表します。
  * `:density`: ビンサイズのみで正規化します。結果として得られるヒストグラムは入力のカウント密度を表し、ノルム1を持ちません。すでに密度を表している場合（`h.isdensity == 1`）、ヒストグラムは変更されません。
  * `:probability`: 重みの合計のみで正規化します。結果として得られるヒストグラムは各ビンの確率質量の割合を表し、ノルム1を持ちません。
  * `:none`: 正規化しません。

**`offset`** =  `0.0`  — すべての値にオフセットを追加します。

**`over_background_color`** =  `automatic`  — *ドキュメントは利用できません。*

**`over_bar_color`** =  `automatic`  — *ドキュメントは利用できません。*

**`scale_to`** =  `nothing`  — すべての値を特定の高さにスケールすることを許可します。これは、ヒストグラムバーの方向を共通の高さにスケールせずに反転させるために`:flip`に設定することもできます。

**`strokecolor`** =  `@inherit patchstrokecolor`  — *ドキュメントは利用できません。*

**`strokewidth`** =  `@inherit patchstrokewidth`  — *ドキュメントは利用できません。*

**`weights`** =  `automatic`  — 観測値に統計的な重みを付けることを許可します。
