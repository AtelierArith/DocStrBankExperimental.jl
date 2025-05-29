```
grdinterpolate(cmd0="", arg1=nothing, arg2=nothing; kwargs...)
```

3-Dデータキューブまたは2-Dグリッドのスタックから、3-Dキューブ、2-Dグリッド、または1-D系列を補間します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdinterpolate`](http://docs.generic-mapping-tools.org/latest//grdinterpolate.html)を参照してください。

## パラメータ

  * **D** | **meta** | **metadata** :: [Type => Str | NamedTuple]  

    xname、yname、zname（キューブの3次元）、およびdname（データ値名）の値の1つ以上の組み合わせを指定し、それらの変数の名前とその単位を角括弧内に示します。
  * **E** | **crossection** :: [Type => Str | GMTdtaset | NamedTuple]

    ファイルまたは指定された線の座標と修飾子から断面プロファイルを指定します。ファイルの場合、lon latまたはlon lat distレコードを含む単一のセグメントでなければなりません。これらは等間隔である必要があります。
  * **F** | **interp_type** | **interpolator** :: [Type => Str]   $Arg = l|a|c|n[+1|+2]$

    l（線形）、a（秋間スプライン）、c（自然立方スプライン）、n（補間なし：最近接点）から選択します。[デフォルトは秋間スプラインです。]
  * **G** | **outfile** | **outgrid** :: [Type => Str]

    出力ファイル名。`range`が単一の層のみを選択する場合、データキューブは通常の2-Dグリッドファイルに崩れます。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **pt** | **track** :: [Type => Str | Tuple | Dataset]	`Arg = x/y|pointfile[+hheader]`

    グリッド出力を計算するのではなく、指定された点（x/y）またはpointfile内の点のリストを通じてスタックされたグリッドを介してタイル/空間系列を作成します。
  * **T** | **range** :: [Type => Str]			`Arg = [min/max/]inc[+i|n] |-Tfile|list`

    minからmaxまでの均等に間隔を空けた時間ステップを作成します。[デフォルトは入力時間を使用します。]
  * **Z** | **levels** :: [Type => range]			`Arg = [levels]`

    `levels`は`range`と同じ方法で指定できます。指定されていない場合、0から始まる整数レベル配列がデフォルトとなります。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します（セカンダリ入力は常にASCIIです）。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目がnodataに等しい場合、この値を欠損データ項目として解釈し、値NaNに置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含むASCIIデータレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べ、ラインにブレークを課すために使用します。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにbを追加することでグリッド補間モードを選択します。cはバイキュービック補間、lはバイリニア補間、nは最近接値です。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    プライマリ出力の特定のデータ列を任意の順序で選択します。
  * **q** | **inrow** | **inrows** :: [Type => Str]       $Arg = [i|o][~]rows[+ccol][+a|f|s]$

    読み取る特定のデータ行を選択します（-qi [デフォルト]）または書き込みます（-qo）[すべて]。
  * **s** | **skiprows** | **skip_NaN** :: [Type => Str]       $Arg = [cols][a|r]$

    z値がNaNに等しいレコードの出力を抑制します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で1列目と2列目を入れ替えます。

2つの数値入力を使用し、`outfile`オプションがない場合、x、yおよびグリッドの順序は重要ではありません。つまり、次の両方が機能します：$D = grdinterpolate([0 0], G);$  または  $D = grdinterpolate(G, [0 0]);$

`pt`または`crossection`オプションを使用する場合、デフォルトは冗長な水平x、y座標を出力しないことです（GMTのデフォルトとは異なります）。それらを持ちたい場合は、オプション`colinfo`を使用します。*例* `colinfo="0-3"`、または`allcols=true`を使用します。

完全なドキュメントを見るには、次のコマンドを入力してください：$@? grdinterpolate$
