```
bracket(x1, y1, x2, y2; kwargs...)
bracket(x1s, y1s, x2s, y2s; kwargs...)
bracket(point1, point2; kwargs...)
bracket(vec_of_point_tuples; kwargs...)
```

各点のペア (x1, y1) と (x2, y2) の間にテキストラベルを中点に配置してブラケットを描画します。

デフォルトでは、各ラベルはブラケットポイント間の線に平行に回転します。

## プロットタイプ

`bracket` 関数のプロットタイプエイリアスは `Bracket` です。

## 属性

**`align`** =  `(:center, :center)`  — *ドキュメントはありません。*

**`color`** =  `@inherit linecolor`  — *ドキュメントはありません。*

**`font`** =  `@inherit font`  — *ドキュメントはありません。*

**`fontsize`** =  `@inherit fontsize`  — *ドキュメントはありません。*

**`joinstyle`** =  `@inherit joinstyle`  — *ドキュメントはありません。*

**`justification`** =  `automatic`  — *ドキュメントはありません。*

**`linecap`** =  `@inherit linecap`  — *ドキュメントはありません。*

**`linestyle`** =  `:solid`  — *ドキュメントはありません。*

**`linewidth`** =  `@inherit linewidth`  — *ドキュメントはありません。*

**`miter_limit`** =  `@inherit miter_limit`  — *ドキュメントはありません。*

**`offset`** =  `0`  — 開始点から終了点への線に垂直なブラケットのオフセット（画面単位）。方向は `orientation` 属性に依存します。

**`orientation`** =  `:up`  — 開始点から終了点への線に対してブラケットがどの方向に伸びるか。`:up` または `:down` です。

**`rotation`** =  `automatic`  — *ドキュメントはありません。*

**`style`** =  `:curly`  — *ドキュメントはありません。*

**`text`** =  `""`  — *ドキュメントはありません。*

**`textcolor`** =  `@inherit textcolor`  — *ドキュメントはありません。*

**`textoffset`** =  `automatic`  — *ドキュメントはありません。*

**`width`** =  `15`  — 開始点から終了点への線から垂直に離れたブラケットの幅（画面単位）。
