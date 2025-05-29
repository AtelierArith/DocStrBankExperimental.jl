```
mask(cmd0::String="", arg1=nothing; kwargs...)
```

データテーブルのカバレッジがないマップエリアをクリップまたはマスクします

完全なGMT（`GMT.jl`ではない）ドキュメントは[`psmask`](http://docs.generic-mapping-tools.org/latest/mask.html)を参照してください

## パラメータ

  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッド間隔です。オプションで、増分単位を追加します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    マップの境界フレームと軸の属性を設定します。
  * **C** | **endclip** | **end*clip*path** :: [Type => Bool]

    既存のクリップパスの終わりをマークします。入力ファイルは必要ありません。
  * **D** | **dump** :: [Type => Str]

    各クリッピングポリゴンの (x,y) 座標を1つ以上の出力ファイル（またはテンプレートが指定されていない場合はstdout）にダンプします。
  * **F** | **oriented** :: [Type => Str | []]

    クリップ輪郭（ポリゴン）がデータポイントの左側（-Fl [デフォルト]）または右側（-Fr）に向くように強制します。
  * **G** | **fill** :: [Type => Number | Str]

    正のマスクおよび/または負のマスクのための塗りつぶしの色、色合い、またはパターンを設定します [デフォルトは塗りつぶしなし]。
  * **J** | **proj** | **projection** :: [Type => String]

    マップの投影を選択します。デフォルトは15x10 cmの線形（非投影）マップです。
  * **Jz** | **zscale** | **zsize** :: [Type => String]
  * **L** | **nodegrid** :: [Type => Str]

    内部グリッドを1（データ制約）と0（データなし）で保存し、指定されたノードグリッドに保存します。
  * **N** | **invert** | **inverse** :: [Type => Bool]

    テストの感覚を反転させます。つまり、データカバレッジがある領域をクリップします。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **Q** | **cut** | **cut_number** :: [Type => Number | Str]

    カット数のポイント未満のポリゴンをダンプしません [すべてのポリゴンをダンプします]。
  * **S** | **search_radius** :: [Type => Number | Str]

    影響の半径を設定します。データポイントの半径内のグリッドノードは信頼できると見なされます。
  * **T** | **tiles** :: [Type => Bool]

    クリップポリゴンの代わりにタイルをプロットします。-Gを使用してタイルの色またはパターンを設定します。-Dと一緒に使用することはできません。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して (x-shift,y-shift) だけシフトし、オプションで長さ単位 (c, i, または p) を追加します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、値NaNに置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **p** | **view** | **perspective** :: [Type => Str or List]   $Arg = [x|y|z]azim[/elev[/zlevel]][+wlon0/lat0[/z0]][+vx0/y0]$

    視点の視点を選択し、方位角と高度を設定します [180/90]。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **t** | **alpha** | **transparency** :: [Type => Str]   $Arg = transp$

    オーバーレイのPDF透明度レベルを設定します（0-100]パーセント範囲で。[デフォルトは0、すなわち不透明]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? mask$
