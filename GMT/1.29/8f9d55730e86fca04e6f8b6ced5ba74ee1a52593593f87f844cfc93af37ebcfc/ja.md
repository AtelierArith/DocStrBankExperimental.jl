```
grdcut(cmd0::String="", arg1=[], kwargs...)
```

新しい出力グリッドを生成します。これは入力グリッドのサブリージョンです。サブリージョンは$limits$（-R）で指定され、指定された範囲は入力グリッドの範囲を超えてはいけません（ただし、$extend$を参照してください）。

## パラメータ

  * **E** | **rowlice** | **colslice** :: [Type => Number]

    x列座標またはy行座標に沿った垂直スライスを抽出します。
  * **F** | **clip** | **cutline** :: [Type => Str | GMTdaset | Mx2 array | NamedTuple]	`Arg = array|fname[+c] | (polygon=Array|Str, crop2cutline=Bool, invert=Bool)`

    閉じたポリゴン（ファイルまたはデータセット）を指定します。ポリゴンの外側にあるすべてのグリッドノードはNaNに設定されます。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdcut(....)の形式を使用してください。
  * **img** | **usegdal** | **gdal** :: [Type => Any]

    切り取り操作をGDALによって行うよう強制します。GMTが失敗したりクラッシュしたりする画像に対して機能します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **N** | **extend** :: [Type => Str or []]

    新しい領域が既存の境界を超える場合、グリッドを拡張できるようにします。現在の領域の外にあるノードを初期化するためにノーデータ値を追加します[デフォルトはNaN]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **circ_subregion** :: [Type => Str]    $Arg = [n]lon/lat/radius[unit]$

    原点と半径を指定します。距離単位を追加すると、円の内側または上にあるすべてのグリッドノードがサブセットに含まれるように対応する長方形の領域を決定します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **Z** | **range** :: [Type => Str]       $Arg = [n|N |r][min/max]$

    この領域の外にあるすべてのノードが指定されたz範囲の外にあるように、新しい長方形の領域を決定します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。

完全なドキュメントを見るには、次のように入力してください: $@? grdcut$ ```
