```
rose(cmd0::String="", arg1=nothing; kwargs...)
```

長さと方位のペアを読み取り、風向図（極座標ヒストグラム）をプロットします。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`psrose`](http://docs.generic-mapping-tools.org/latest/rose.html)を参照してください。

## パラメータ

  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは15x10 cmの線形（非投影）地図です。
  * **A** | **sector** | **sectors** :: [Type => Str | Number]

```
セクターとローズ図のセクター幅を度単位で指定します。
```

  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **color** :: [Type => Str | GMTcpt]

```
CPTを指定します。各バーの中間x値を使用してバーの色を検索します。
```

  * **E** | **vectors** :: [Type => Str]

```
mode_fileファイルに指定された主な方向を示すベクトルをプロットします。
```

  * **D** | **shift** :: [Type => Bool]

```
セクターをシフトして、ビン間隔の中心に配置します（例：最初のセクターは0度の中心に配置されます）。
```

  * **F** | **no_scale** :: [Type => Bool]

```
スケール長バーを描画しません [デフォルトは右下隅にスケールをプロットします]。
```

  * **G** | **fill** :: [Type => Str | Number]

```
セクターを塗りつぶすためのシェード、色、またはパターンを選択します [デフォルトは塗りつぶしなし]。
```

  * **I** | **inquire** :: [Type => Bool]

```
問い合わせ。役立つ-Rを指定するために必要な統計を計算します。プロットは生成されません。
```

  * **L** | **labels** :: [Type => Str | Number]

```
0、90、180、および270度のマークのラベルを指定します。
```

  * **M** | **vector_params** :: [Type => Str]

```
-Cと共に使用してベクトルパラメータを変更します。
```

  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **alpha** :: [Type => Str | []]

```
平均結果が有意かどうかを判断するために使用される信頼レベルを設定します。
```

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **norm** | **normalize** :: [Type => Bool]

```
プロットされた円の半径を指定します（c|i|pの単位を追加します）。
```

  * **T** | **orientation** :: [Type => Bool]

```
入力データが方向データであることを指定します（すなわち、180度の曖昧さがある） 
真の0-360度の方向ではなく[デフォルト]。
```

  * **W** | **pen** :: [Type => Str | Tuple]

```
セクターのアウトラインまたはローズプロットのペン属性を設定します。[デフォルトはアウトラインなし]。
```

  * **Z** | **scale** :: [Type => Str]

```
データの半径をスケールで乗算します。
```

  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さの単位(c、i、またはp)を追加します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、NaN値に置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位と標高を設定します [180/90]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを(0-100]パーセント範囲で設定します。[デフォルトは0、すなわち不透明]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを周期的な座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。
  * **savefig** | **figname** | **name** :: [Type => Str]

    `figname=name.ext`で図を保存します。ここで`ext`は図の形式を選択します（例：figname="name.png"）

完全なドキュメントを見るには、次のように入力してください: $@? rose$
