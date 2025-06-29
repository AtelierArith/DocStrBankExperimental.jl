```
D = polygonize(data::GItype; kwargs...) -> Vector{GMTdataset}
```

このメソッドは、GDALのGDALPolygonize関数を使用して、ラスタ内の共通のピクセル/セル値を持つすべての接続されたピクセル領域のベクターポリゴンを作成します。入力はグリッドまたは画像である可能性があります。この関数は、色の遷移間でわずかに異なる値を持つピクセルに多くのポリゴンを選択するため、かなり遅くなることがあります。自然な使用法は、マスク画像をデジタル化することです。

### 引数

  * `data`: 入力データ。GMTgridまたはGMTimageオブジェクトである可能性があります。

### キーワード引数

  * `min, nmin, npixels または ncells`: ポリゴンを保持するための最小セル/ピクセル数。デフォルトは1です。これを設定することで、小さなポリゴンをフィルタリングできます。
  * `min_area`: ポリゴンを保持するための最小面積（m2）。このオプションは、セルのカウントに基づく上記のものよりも優先されます。また、これはおおよその値であることに注意してください。なぜなら、この時点ではポリゴンの緯度を正確に知らないからです。
  * `max_area`: ポリゴンを保持するための最大面積（m2）。
  * `simplify`: ポリゴンにDouglas-Peucker線簡略化アルゴリズムを適用します。メートル単位での許容誤差を提供します。例えば: `simplify=0.5`。ただし、あまりにも大きな許容誤差は、他の良好なポリゴンの喪失につながる可能性があるため、注意が必要です。良い目安は、許容誤差にセルサイズを使用することです。実際、`simplify=:auto`を使用する際にはそれを行います。
  * `sort`: trueの場合、ピクセル数でポリゴンをソートします。デフォルトはGDALが内部で決定する順序です。
