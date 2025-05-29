```
fill_between(D1 [,D2]; kwargs...)
```

2つの水平曲線の間の領域を塗りつぶします。

曲線は、行列またはGMTdataset `D1`内の点 (x, y1, y2) によって定義されます。これにより、塗りつぶされた領域を説明する1つまたは複数のポリゴンが作成されます。代わりに、2番目の行列 `D2`（またはスカラー y=cte）を指定すると、ポリゴンは曲線 `D1` と `D2` の交点から構築されます。

  * `fill_between(..., fill=colors)`: '上' と '下' のポリゴンを塗るための2つの色のリストを指定します。
  * `fill_between(..., fillalpha=[alpha1,alpha2])`: 2つのポリゴンセットの透明度を設定します（デフォルトは60%）。
  * `fill_between(..., pen=...)`: 2つの曲線のペンスペックを設定します。最も簡単なのは、`plot()`モジュールで使用されるように、線の太さ、色、スタイルのショートカット `lt`、`lc`、`ls` を使用することです。
  * `fill_between(..., stairs=true)`: 代わりに階段曲線をプロットします。
  * `fill_between(..., markers=true)`: データの位置にマーカーポイントを追加します。
  * `fill_between(..., white=true)`: 曲線と塗りつぶしの間に薄い白い境界線を描きます。
  * `fill_between(..., labels=...)`: 凡例で使用するラベルを渡します。

      * `labels=true` は `D1` と `D2` の列名を使用します。
      * `labels="Lab1,Lab2"` または `labels=["Lab1","Lab2"]`（この形式はタプルでも可）は、`Lab1`、`Lab2` のテキストを使用します。
  * `fill_between(..., legend=...)`: 上記の `labels` として使用される場合、同様に動作しますが、その引数は `legend=(labels="Lab1,Lab2", position=poscode, box=(...))` のような名前付きタプルでも可能です。

例:

```
theta = linspace(-2π, 2π, 150);
y1 = sin.(theta) ./ theta;
y2 = sin.(2*theta) ./ theta;
fill_between([theta y1], [theta y2], white=true, legend="Sinc1,Sinc2", show=1)
```
