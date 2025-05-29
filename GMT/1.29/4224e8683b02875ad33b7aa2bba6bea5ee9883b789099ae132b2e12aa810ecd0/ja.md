```
gmtwrite(fname::AbstractString, data; kwargs...)
```

GMTオブジェクトをファイルに書き込みます。オブジェクトは「grid」または「grd」、「image」または「img」、「dataset」または「table」、「cmap」または「cpt」、および「ps」（ポストスクリプト用）です。

グリッド、画像、データセットを保存する際には、さまざまなフォーマットを利用できます。データセットの場合、ファイル名が .arrow、.shp、.json、.feather、.geojson、.gmt、.gpkg、.gpx、.gml、または .parquet で終わると、自動的に $gdalwrite$ を選択し、そのOGRベクターフォーマットでGMTデータセットを保存します。.kmlは特別なケースとして扱われ、KML形式のデータを生成するGMTモジュール（例：`gmt2kml`）があるため、テキストファイルとして直接書き込みます。

## パラメータ

  * `binary`: `stl`ファイルを保存する際にのみ適用されます。デフォルトはtrueです。`binary=false`を使用してasciiで保存します。
  * `id`:  [Type => Str] 

    標準のCOARDS準拠のnetCDFグリッドにグリッドを保存しない場合に$ id $コードを使用します。この$ id $は、ESRI Arc/Info ASCII Grid Interchange形式（ASCII float）で保存するための$ ef :のような2文字で構成されています。完全なidのリストはhttp://docs.generic-mapping-tools.org/latest/grdconvert.html#format-identifierを参照してください。

    (http://docs.generic-mapping-tools.org/latest/grdconvert.html#g)
  * `scale` | `offset`: [Type => Number]

    データをスケーリングし、指定された量でオフセットするようにオプションで要求できます。これらの修飾子は、オフセットを削除し、値をスケーリングダウンすることで、整数としてデータを保存する際に特に便利です。`scale`因子は、stlに保存する際にも適用できます（z値をスケーリングします）。
  * `nan` | `novalue` | `invalid` | `missing`: [Type => Number]

    無効なグリッドエントリを表す値、すなわち「Not-a-Number」を提供できます。
  * `gdal`: [Type => Bool]

    グリッドを書き込むためにGDALライブラリの使用を強制します（グリッドにのみ使用）。   (http://docs.generic-mapping-tools.org/latest/GMT_Docs.html#grid-file-format-specifications)
  * `driver`: [Type => Str]

    netCDF形式以外で保存する場合、GDALライブラリに希望する形式を伝える必要があります。それは、GDAL自体が使用するドライバ名を指定することで行います（例：netCDF、GTiFFなど）。
  * `datatype`: [Type => Str] 		$Arg = u8|u16|i16|u32|i32|float32$

    GDALで保存する際に、u8|u16|i16|u32|i32|float32からデータ型を指定できます。ここで「i」と「u」はそれぞれ符号付きおよび符号なし整数を示します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。

例：GMTgrid 'G'オブジェクトを'lixo.grd'というncファイルに書き込む

```
gmtwrite("lixo.grd", G);
```
