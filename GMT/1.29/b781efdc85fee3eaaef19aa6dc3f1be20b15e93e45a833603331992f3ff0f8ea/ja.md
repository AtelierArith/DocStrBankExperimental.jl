```
gmtread(fname::String; kwargs...)
```

ファイルからGMTオブジェクトを読み込みます。オブジェクトは「grid」または「grd」、「image」または「img」、「data」または「table」、「cmap」または「cpt」、および「ps」（PostScript用）とOGRフォーマット（shp、kml、json）のいずれかです。特定の読み取りパスを強制するために型指定を使用することができます（例：`grd=true`でグリッドを読み取る）またはファイル拡張子によってデータ型を推測させることができます。既知の拡張子は次のとおりです：

  * グリッド:      .grd .jp2 .nc
  * 画像:         .jpg .jp2 .png, .tif, .tiff, .bmp, .webp
  * データセット: .dat .txt .csv .isf
  * データセット: .arrow .arrows .shp .kml .kmz .json .gmt .feather .fgb .gpkg .geojson .gpx .gml .ipc .parquet .sqlite
  * CPT:          .cpt
  * PostScript:   .ps, .eps

## パラメータ

データ型を指定します（*type*=true、例：`img=true`）。次の中から選択します：

  * `grd` | `grid`: グリッドを読み込む。
  * `img` | `image`: 画像を読み込む。
  * `cpt` | `cmap`: GMTカラーパレットを読み込む。
  * `data` | `dataset` | `table`: データセット（数値の表）を読み込む。
  * `ogr`: GDAL OGRを介してデータセットを読み込む（数値の表）。ここでは多くのことが起こり得ます。
  * `ps`: PostScriptファイルを読み込む。
  * `gdal`: GDALを介してファイルを強制的に読み込む。グリッドを読み取るためだけに使用するべきです。
  * `varname`: netCDFファイルに2D（またはそれ以上）の変数が複数ある場合、*varname*を使用して希望の変数を選択します。例：$varname=:slp$で$slp$という名前の変数を読み取ります。このオプションはデータ型を`grid`にデフォルト設定します。このオプションは`gdal`オプションとともに、またはなしで使用できます。前者の場合、GMTライブラリを使用してキューブを読み取り、列優先順序の3D配列を出力します。後者の場合（`gdal`を使用する場合）、GDALを使用してキューブを読み取り、行優先順序の3D配列を出力します。$layout$メンバーはGMTgrid型のメモリレイアウトについて通知します。
  * `inrows`: 読み取る特定のデータ行を選択します。有効な引数には範囲またはハードコアGMT -qオプションを含む文字列があります。
  * `nodata`: GMTを介してテーブルデータを読み取る際（ただしGDALではない）、このオプションによりユーザーがコーディングした欠損データ値をNaN値に変換できます。デフォルトでは最初の2列の後のすべての入力列を調べます。+c修飾子を使用して調査に使用される開始列を上書きします。例：`nodata=-99999+c1`で2列目のすべての-99999値をNaNsに置き換えます。
  * `stride`: GMTを介してテーブルデータを読み取る際（ただしGDALではない）、このオプションによりデータのサブサンプリングが可能になります。行のストライドとして使用する数を提供します。`stride=2`は、毎回別の行を読み取ります。
  * `layer`| `layers` | `band` | `bands`: 文字列、数値、または配列。ファイルがマルチバンドまたは3Dまたは4D配列を持つncファイルの場合、これらのキーワードを介してアクセスします。`layer=4`はファイルの4番目のレイヤー（またはバンド）を読み取ります。ファイルはグリッドまたは画像である可能性があります。グリッドの場合、レイヤーはスカラー（3D配列を読み取るため）または2要素の配列（4D配列を読み取るため）であることができます。`layers=:all`を使用してすべてのレイヤーを読み取ります。

    ファイルが画像の場合、`layer`は1または1x3配列（RGB画像を読み取るため）であることができます。この場合、バンドは連続している必要はありません。`band=[1,5,2]`はこれらのバンドからRGBを構成します。詳細はhttp://docs.generic-mapping-tools.org/latest//GMT_Docs.html#modifiers-for-coards-compliant-netcdf-filesを参照してください。ただし、ここでは**1ベース**のインデックスを使用します。

    $$
    layers=:all
    $$

    を使用して3DキューブnetCDFファイルのすべてのレベルを読み取ります。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信するための冗長性レベルを選択します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。

例：'lixo.grd'というncを読み取るには

```
G = gmtread("lixo.grd");
```

バンドを反転させたjpg画像を読み取るには

```
I = gmtread("image.jpg", band=[2,1,0]);
```
