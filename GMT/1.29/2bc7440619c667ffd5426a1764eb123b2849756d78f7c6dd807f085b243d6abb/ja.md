```
G = gridit(fname="", indata=nothing; method="surface", gdopts="", proj="", epsg=0, kw...)
```

散発データをグリッドに補間するためのラッパー関数。補間方法はGMTおよびGDAL（gdal_grid）のものが使用できます。

### パラメータ

  * `fname`: 補間するソースデータセットを含むファイル名。少なくとも3列（x y z）を含む必要があります。
  * `indata`: GMTdataset、Mx3行列、またはGDALデータセットの形式の代替ソースデータセット。
  * `method`: 補間方法の名前。次のいずれか（GMT）: "surface" または "minimum curvature", "triangulate", "nearneighbor", "sphtriangulate", "greenspline"。引数: "mean", "median", "mode", "std", "highest", "lowest" は、各 *rectangular* セル内でそれらの量を計算します。

      * または（GDAL）: "invdist", "invdistnn", "average", "nearest", "linear", "minimum", "maximum", "range",

    "count", "average*distance", "average*distance*pts"。詳細は https://gdal.org/programs/gdal*grid.html#gdal-grid を参照してください。

      * さまざまな方法の間には重複があることに注意してください。たとえば、GMTの $nearneighbor$ とGDALの $invdist$ は同じアルゴリズム（逆距離加重）を適用しますが、加重平均を行うためのポイントの選択方法が異なります。
  * `gdopts`: gdal_gridユーティリティによって受け入れられるオプションのリスト。これはGDALメソッドにのみ適用されます。
  * `proj`: データの座標系を説明するオプションのproj4文字列。このオプションはデータの投影を意味するものではありません。入力データ自体がこの情報をすでに持っている場合、このオプションは必要ありません。
  * `wkt`: データの座標系を説明するオプションのwkt文字列。`proj`と同様のコメント。
  * `epsg`: データの座標系を説明するオプションのepsgコード。`proj`と同様のコメント。

# Kwargs

  * `kw...` keyword=value 引数。これらは特定のGMT補間方法に特有のオプションを渡すために使用されます。ユーザーは利用可能な可能性について学ぶために個別のマニュアルページを参照する必要があります。非常に重要な（実際には必須の）*オプション*は、グリッドの制限とグリッドの解像度を選択する `region=...` と `inc=...` です。ただし、これらが提供されていない場合（またはそのうちの1つのみが提供されている場合）、データの制限とポイント密度に基づいて非常に粗い推定を行います。しかし、これは非常に探索的な計算にのみ使用されるべきです。
  * `preproc`: このオプションは `method=:surface` にのみ適用され、データが $surface$ プログラムによって強く推奨されるように、各セル内のデータを減少させるために $block*$ モジュールの1つを通過することを意味します。`preproc=true` は $blockmean$ を使用します。他の2つのいずれかを使用するには、その名前を値として渡します。*例* `preproc="blockmedian"`。

### 戻り値

GMTgrid または、ファイルがディスクに書き込まれた場合は何も返しません。

### 例

```
G = gridit("@ship_15.txt", method=:surface, mask=0.3, preproc=true);
```
