Legendには以下の属性があります：

`alignmode` デフォルト: `Inside()` 親GridLayout内の凡例の整列モード。

`bgcolor` デフォルト: `:white` 凡例の背景色。

`colgap` デフォルト: `16` 1つの凡例エントリのラベルと次のパッチの間の隙間。

`framecolor` デフォルト: `:black` 凡例の境界の色。

`framevisible` デフォルト: `true` 凡例の境界が表示されるかどうかを制御します。

`framewidth` デフォルト: `1.0` 凡例の境界の線の幅。

`gridshalign` デフォルト: `:center` 親GridLayout内のエントリグループの水平方向の整列。

`gridsvalign` デフォルト: `:center` 親GridLayout内のエントリグループの垂直方向の整列。

`groupgap` デフォルト: `16` 各グループと次のグループの間の隙間。

`halign` デフォルト: `:center` 提案された境界ボックス内の凡例の水平方向の整列。

`height` デフォルト: `Auto()` 凡例の高さ設定。

`label` デフォルト: `"undefined"` デフォルトのエントリラベル。

`labelcolor` デフォルト: `lift_parent_attribute(scene, :textcolor, :black)` エントリラベルの色。

`labelfont` デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")` エントリラベルのフォントファミリー。

`labelhalign` デフォルト: `:left` エントリラベルの水平方向の整列。

`labelsize` デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)` エントリラベルのフォントサイズ。

`labelvalign` デフォルト: `:center` エントリラベルの垂直方向の整列。

`linepoints` デフォルト: `[Point2f0(0, 0.5), Point2f0(1, 0.5)]` 各ラベルパッチに対する正規化された座標でのLineElementsに使用されるデフォルトのポイント。

`linewidth` デフォルト: `3` LineElementsに使用されるデフォルトの線の幅。

`margin` デフォルト: `(0.0f0, 0.0f0, 0.0f0, 0.0f0)` 凡例と提案された境界ボックスの間の追加スペース。

`markerpoints` デフォルト: `[Point2f0(0.5, 0.5)]` 各ラベルパッチに対する正規化された座標でのMarkerElementsに使用されるデフォルトのマーカーポイント。

`markersize` デフォルト: `12` MarkerElementsに使用されるデフォルトのマーカーサイズ。

`markerstrokewidth` デフォルト: `1` MarkerElementsに使用されるデフォルトのマーカーストローク幅。

`nbanks` デフォルト: `1` 凡例エントリがグループ化されるバンクの数。凡例が垂直に配置されている場合は列、そうでない場合は行。

`orientation` デフォルト: `:vertical` 凡例の向き（`:horizontal`または`:vertical`）。

`padding` デフォルト: `(10.0f0, 10.0f0, 8.0f0, 8.0f0)` 凡例の内容と境界の間の追加スペース。

`patchcolor` デフォルト: `:transparent` 凡例マーカーを含むパッチの色。

`patchlabelgap` デフォルト: `5` 各凡例エントリのパッチとラベルの間の隙間。

`patchsize` デフォルト: `(20.0f0, 20.0f0)` 凡例マーカーを含む長方形のサイズ。

`patchstrokecolor` デフォルト: `:transparent` 凡例マーカーを含むパッチの境界の色。

`patchstrokewidth` デフォルト: `1.0` 凡例マーカーを含むパッチの境界の線の幅。

`polypoints` デフォルト: `[Point2f0(0, 0), Point2f0(1, 0), Point2f0(1, 1), Point2f0(0, 1)]` 各ラベルパッチに対する正規化された座標でのPolyElementsに使用されるデフォルトのポリポイント。

`polystrokewidth` デフォルト: `1` PolyElementsに使用されるデフォルトのポリストローク幅。

`rowgap` デフォルト: `3` エントリ行の間の隙間。

`tellheight` デフォルト: `false` 親レイアウトがこの要素の高さに調整できるかどうかを制御します。

`tellwidth` デフォルト: `true` 親レイアウトがこの要素の幅に調整できるかどうかを制御します。

`titlecolor` デフォルト: `lift_parent_attribute(scene, :textcolor, :black)` 凡例のタイトルの色。

`titlefont` デフォルト: `lift_parent_attribute(scene, :font, "DejaVu Sans")` 凡例グループタイトルのフォントファミリー。

`titlegap` デフォルト: `8` 各グループタイトルとそのグループの間の隙間。

`titlehalign` デフォルト: `:center` 凡例グループタイトルの水平方向の整列。

`titleposition` デフォルト: `:top` グループタイトルの位置はそのグループに対して相対的です。`:top`または`:left`にできます。

`titlesize` デフォルト: `lift_parent_attribute(scene, :fontsize, 16.0f0)` 凡例グループタイトルのフォントサイズ。

`titlevalign` デフォルト: `:center` 凡例グループタイトルの垂直方向の整列。

`titlevisible` デフォルト: `true` 凡例のタイトルが表示されるかどうかを制御します。

`valign` デフォルト: `:center` 提案された境界ボックス内の凡例の垂直方向の整列。

`width` デフォルト: `Auto()` 凡例の幅設定。
