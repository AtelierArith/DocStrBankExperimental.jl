```
greenspline(cmd0::String="", arg1=nothing; kwargs...)
```

ランダムに間隔を空けた (x,y,z) トリプルを読み込み、次の式を解くことによってグリッド化された値 z(x,y) のバイナリグリッドファイルを生成します：

```
	(1 - T) * L (L (z)) + T * L (z) = 0
```

完全な GMT (GMT.jl ではない) ドキュメントは [`greenspline`](http://docs.generic-mapping-tools.org/latest/greenspline.html) を参照してください。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **I** | **inc** :: [Type => Str | Number]

    *x_inc* [およびオプションで *y_inc*] はグリッド間隔です。
  * **A** | **gradient** :: [Type => Str | Array]		$Arg = gradfile+f1|2|3|4|5 | (data=Array, format=x)$

    解は、v = v*n という表面勾配によって部分的に制約されます。ここで、v は勾配の大きさで、n はその単位ベクトルの方向です。
  * **C** | **approx** | **approximate** :: [Type => Str | Number]	$Arg = [n]value[+ffile]$

    おおよその表面フィットを見つけます：スプライン係数のための線形システムを SVD で解き、最大固有値に対する比率が value より小さいすべての固有値からの寄与を排除します。
  * **G** | **grid** :: [Type => Str | []]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = greenspline(....) 形式を使用してください。
  * **D** | **metadata** | **mode** :: [Type => Number]

    データポイント間の距離を計算する方法を決定する距離フラグを設定します。
  * **E** :|**misfit** :: [Type => Str | []]		$Arg = [misfitfile]$

    入力データの位置でスプラインを正確に評価し、ミスフィットの統計（平均、標準偏差、rms）を報告します。
  * **L** | **leave_trend** :: [Type => Bool]

    -D がモード 0-3 を選択したときに線形 (1-D) または平面 (2-D) トレンドを削除しません。
  * **N** | **nodes** :: [Type => Number | Array]			$Arg = nodefile$

    最初の列に出力位置 x の座標を持つ ASCII ファイル。
  * **Q** | **dir_derivative** :: [Type => Str]		$Arg = az|x/y/z$

    表面を評価するのではなく、az 方位で方向微分を取り、この微分の大きさを返します。
  * **S** | **splines** :: [Type => Str]				$Arg = c|t|l|r|p|q[pars]$

    6 つの異なるスプラインのいずれかを選択します。最初の 2 つは 1-D、2-D、または 3-D カルテシアン スプラインに使用されます。
  * **T** | **mask** :: [Type => Str]					$Arg = maskgrid$

    2-D 補間のみに使用されます。NaN に等しくない maskgrid のノードでのみ解を評価します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートを stderr に送信する冗長性レベルを選択します。
  * **W** | **uncertainties** :: [Type => Str | []]	$Arg = [w]$

```
データの一シグマ不確実性は最後の列に提供されます。次に、不確実性の二乗に反比例する重みを計算します。
```

  * **Z** | **mode** | **distmode** :: [Type => Str | number]

    データポイント間の距離を計算する方法を決定する距離モードを設定します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値が GMT の公式 NaN 値にどのように変換されるかを制御します。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します（時間または地理データ）。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    プライマリ出力の特定のデータ列を任意の順序で選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    OpenMP 対応のマルチスレッドアルゴリズムで使用されるコアの数を制限します。 (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で 1 列目と 2 列目を入れ替えます。

完全なドキュメントを見るには、次のように入力してください： $@? greenspline$
