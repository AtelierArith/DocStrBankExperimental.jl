```
xyz2grd(cmd0::String="", arg1=nothing; kwargs...)
```

データテーブルをグリッドファイルに変換します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`xyz2grd`](http://docs.generic-mapping-tools.org/latest/xyz2grd.html)を参照してください。

## パラメータ

  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで*y_inc*]はグリッドの間隔です。オプションで、増分単位を追加できます。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **A** | **multiple_nodes** :: [Type => Str]      `Arg = [d|f|l|m|n|r|S|s|u|z]`

    デフォルトでは、複数のエントリが同じノードに落ちる場合、平均値を計算します。この動作を変更するにはAを使用します。
  * **D** | **header** :: [Type => Str]  `Arg = [+xxname][+yyname][+zzname][+sscale][+ooffset][+ninvalid][+ttitle][+rremark]`

    出力エッジ
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdclip(....)形式を使用してください。
  * **J** | **proj** | **projection** :: [Type => String]

    地図投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **S** | **swap** :: [Type => Str | []]        `Arg = [zfile]`

    入力のバイトオーダーのみをスワップします。グリッドファイルは生成されません。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **Z** | **flags** :: [Type => Str]

    1列のテーブルを読み取ります。これは、すべてのノードが存在し、指定された順序規則に従ってソートされていると仮定します。$flags$に含まれています。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、値NaNに置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? xyz2grd$
