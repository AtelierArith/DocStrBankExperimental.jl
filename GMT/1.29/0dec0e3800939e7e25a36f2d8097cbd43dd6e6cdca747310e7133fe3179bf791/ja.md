```
surface(cmd0::String="", arg1=nothing; kwargs...)
```

ランダムに間隔を空けた (x,y,z) トリプルを読み込み、次の方程式を解くことによってグリッド化された値 z(x,y) のバイナリグリッドファイルを生成します：

```
	(1 - T) * L (L (z)) + T * L (z) = 0
```

完全な GMT ( `GMT.jl` ではない) ドキュメントは [`surface`](http://docs.generic-mapping-tools.org/latest/surface.html) を参照してください。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッドの間隔です。オプションで、増分単位を追加できます。
  * **A** | **aspect_ratio** :: [Type => Number]

    アスペクト比。必要に応じて、方程式にグリッドの異方性を追加できます。
  * **C** | **convergence** :: [Type => Number]

    収束限界。任意のグリッド値の最大絶対変化が収束限界未満になったとき、反復は収束したと見なされます。
  * **D** | **breakline** :: [Type => String | NamedTuple]     `Arg = breakline[+z[level]] | (data=Array, [zlevel=x])`

    ブレークラインファイルの xyz データを「ソフトブレークライン」として使用します。これは、頂点が最近接グリッドノードを制約するために使用され、さらなる補間は行われません。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合にのみ使用されます。それ以外の場合は、G = surface(....) 形式を使用してください。
  * **Ll** | **lower** :: [Type => Str | Number]

    出力解に制限を課します。lower は下限を設定します。lower は下限値を持つグリッドファイルの名前、固定値、または最小入力値に設定する d であることができます。
  * **Lu** | **upper** :: [Type => Str | Number]
  * **M** | **mask** :: [Type => Number]      `Arg = max_radius`

    サーフェスの解決後、データ制約から max_radius 以上離れたノードを NaN に設定するマスクを適用します。
  * **N** | **iterations** | **max_iterations** :: [Type => Number]

    反復の数。収束*限界に達するか、反復の数が max*iterations に達するまで反復は続きます。
  * **Q** | **suggest** :: [Type => Bool]

    非常に合成的な最大公約数を持つグリッドの次元を提案します。
  * **S** | **search_radius** :: [Type => Number | Str]  

    作成される投影グリッドの解像度を設定します。
  * **T** | **tension** :: [Type => Number | Str]

    テンション係数[s]。これらは 0 と 1 の間でなければなりません。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告を stderr に送信する冗長性レベルを選択します。
  * **W** | **log** :: [Type => Str]

    収束情報をログファイル [surface_log.txt] に書き込みます。
  * **Z** | **over_relaxation** :: [Type => Str | GMTgrid]

    過剰緩和係数。このパラメータは収束を加速するために使用され、1 と 2 の間の数値です。
  * **preproc** :: [Type => Bool | Str/Symb]

    このオプションは、データが以前に $block*$ モジュールのいずれかを通過して、各セル内のデータを強く減少させることを意味します。 `preproc=true` は $blockmean$ を使用します。他の 2 つのいずれかを使用するには、その名前を値として渡します。 *例* `preproc="blockmedian"`。
  * **a** | **aspatial** :: [Type => Str]			$Arg = [col=]name[…]$

    GMT における非空間データの入力および出力時の処理方法を制御します。
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    主入力のネイティブバイナリ形式を選択します (二次入力は常に ASCII です)。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目が nodata と等しい場合、この値を欠損データ項目として解釈し、値 NaN に置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します (時間または地理データ)。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主入力ファイルにヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    主入力の特定のデータ列を任意の順序で選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを周期的な座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力時に 1 番目と 2 番目の列を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? surface$
