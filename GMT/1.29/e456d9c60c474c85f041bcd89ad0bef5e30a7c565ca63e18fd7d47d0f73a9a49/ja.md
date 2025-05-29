```
plotgrid!(GI, grid; annot=true, sides="WESN", fmt="", figname="", show=false)
```

`worldrectangular` 関数で作成された画像の上にグリッド線をプロットします。

  * `GI`: GMTgrid または GMTimage データ型。
  * `grid`: プロットする子午線と緯線の GMTdataset のベクター。これは通常、`graticules()` または `worldrectgrid()` 関数によって生成されます。
  * `annot`: 座標注釈をプロットするかどうか (`annot=false`)。
  * `sides`: プロットのどの側面に注釈を付けるか。`W` または `L` は左側を注釈付けすることを意味し、"WESNLRBT" の任意の組み合わせに対して同様です。特定の側面に注釈を付けたくない場合は、その文字を省略してください。*例* `sides="WS"` は左側と下側の軸のみを注釈付けします。
  * `figname`: ローカルディレクトリに `figname` という名前の図を作成します。`figname` に拡張子がある場合、それを使用して図の形式を選択します。*例* `figname=fig.pdf` はローカルに 'fig.pdf' という名前の PDF ファイルを作成します。
  * `fmt`: `format` 形式でラスタ図を作成します。デフォルトは `fmt=:png` です。PDF 形式で取得するには `fmt=:pdf` を使用します。
  * `show`: `true` の場合、図を完成させて表示します。
