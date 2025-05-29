```
grd2xyz(cmd0::String="", arg1=nothing, kwargs...)
```

1つの2次元グリッドを読み取り、xyzトリプレットを返します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grd2xyz`](http://docs.generic-mapping-tools.org/latest/grd2xyz.html)を参照してください。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **C** | **row_col** | **rowcol** :: [Type => Bool]

    出力のx座標とy座標を対応する列番号と行番号に置き換えます。
  * **L** | **hvline** :: [Type => String]

    レコードの出力を単一の行または列に制限します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **T** | **stl** | **STL** :: [Type => String]

    3Dプリント用のSTL三角形分割を計算します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **W** | **weight** :: [Type => Str]           `Arg = [a|weight]`

    x,y,z,wを書き出します。ここでwは提供された重み（提供されていない場合は1）です。[デフォルトはx,y,zのみを書き出します]。
  * **Z** | **onecol** | **one_col** :: [Type => Str]

    1列のテーブルを書き出します。出力は$flags$に含まれる指定された順序規則に従って整理されます。
  * **write** | **|>** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に返すのではなく、ASCIIファイルに保存します。ファイル名を引数として指定します。boオプションを使用してバイナリファイルとして保存します。
  * **append** :: [Type => Str]     $Arg = fname$

    結果をJulia変数に返すのではなく、$fname$という名前の既存のファイルに追加します。boオプションを使用してバイナリファイルとして保存します。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    プライマリ出力の特定のデータ列を任意の順序で選択します。
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    z値がNaNに等しいレコードの出力を抑制します。
