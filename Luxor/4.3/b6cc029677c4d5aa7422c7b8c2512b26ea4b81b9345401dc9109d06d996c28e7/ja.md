```
text(str)
text(str, pos)
text(str, pos, angle = pi/2)
text(str, x, y)
text(str, pos, halign = :left)
text(str, valign = :baseline)
text(str, valign = :baseline, halign = :left)
text(str, pos, valign = :baseline, halign = :left)
text(latexstr, pos, valign = :baseline, halign = :left, rotationfixed = false, angle = 0)
text(typststr, pos::Point, place=true, centered=false, preamble=typststr)
```

文字列 `str` のテキストを `x`/`y` または `pt` に描画し、文字列の開始点をその位置に配置します。ポイントを省略すると、現在の `0/0` に配置されます。

`angle` は、現在の x 軸に対するテキストの回転を指定します。

水平方向の整列 `halign` は `:left`、`:center`（または `:centre`）、または `:right` で指定できます。 垂直方向の整列 `valign` は `:baseline`、`:top`、`:middle`、または `:bottom` で指定できます。

デフォルトの整列は `:left`、`：baseline` です。

この関数は Cairo の Toy テキスト API を使用します。

他のテキスト関数：

`textextents()` - 現在のフォントでのテキストの寸法を見つける

`settext()` - `text()` のようですが、Pro API を使用

`setfont()` - `fontface()` のようですが、Pro API を使用

`label()` - オフセットとリーダーラインを持つポイントに対してテキストを描画

`textbox()` - 文字列の配列を垂直に下に描画

`textcurve()` - 円弧上にテキストを描画

`textfit()` - サイズを変更してテキストをバウンディングボックスに収める

`textlines()` - テキストを幅に収まるように文字列の配列に分割

`textonpoly()` - 多角形のエッジに座るテキストを描画

`textpath()` - テキストをパス（直線とベジェセグメント）に変換

`textoutlines()` - テキストをポリゴン（長さの異なる直線）に変換

`textplace()` - フォント/サイズ/位置の仕様に従って文字ごとにテキストを描画

`texttrack()` - トラッキングされたテキストを描画（タイトまたはルーズ）

`textwrap()` - 行を再調整してボックスに収まるようにテキストを描画
