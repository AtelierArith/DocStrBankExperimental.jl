```
grdvector(arg1, arg2, kwargs...)
```

2次元グリッドファイル2つを取り込み、ベクトル場のx成分とy成分を表し、ファイルの情報に基づいて向きと長さを持つベクトルを描画することでベクトル場プロットを生成します。代わりに、極座標r、thetaグリッドを指定することもできます。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdvector`](http://docs.generic-mapping-tools.org/latest/grdvector.html)を参照してください。

## パラメータ

  * **A** | **polar** :: [Type => Bool]  

    グリッドが直交座標（x, y）の代わりに極座標（r, theta）成分を含むかどうか [デフォルトは直交座標成分]。
  * **B** | **frame** | **axis** | **xaxis yaxis**:: [Type => Str] 

    地図の境界フレームと軸の属性を設定します。
  * **C** | **color** | **colormap** | **cmap** | **colorscale** :: [Type => Str]	$Arg = [cpt |master[+izinc] |color1,color2[,*color3*,…]]$

    CPT名を指定するか、-Ccolor1,color2[,color3,...]を指定して、これらの色から自動的に線形連続CPTを構築します。
  * **G** | **fill** :: [Type => Str | Number]

    ベクトル内部の色または陰影を設定します [デフォルトは塗りつぶしなし]。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Sytr | Number]	$Arg=[x]dx[/dy]$

    ノードごとにx*inc、y*incの間隔でのみベクトルをプロットします（元のグリッド間隔の倍数である必要があります）。
  * **maxlen** :: [Type => Number]

    矢印が持つ最大の長さをプロット単位で設定します。デフォルトではfigの幅/20に等しいです。

```
このオプションは**inc**が設定されている場合は無視されます。
```

  * **N** | **noclip** | **no_clip** :: [Type => Bool]

    地図の境界外にあるシンボルをクリップしない
  * **Q** | **vec** | **vector** | **arrow** :: [Type => Str]

    ベクトルパラメータを変更します。ベクトルヘッドのサイズを追加します [デフォルトは0、すなわちスティックプロット]。
  * **P** | **portrait** :: [Type => Bool or []]

    GMTにポートレートモードで描画しないように指示します（つまり、ランドスケーププロットを作成します）。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **vscale** | **vec_scale** :: [Type => Str | Number]		$Arg = [i|l]scale[unit]$

    プロット距離測定単位あたりのデータ単位でのベクトルプロットの長さのスケールを設定します [1]。
  * **T** | **sign_scale** :: [Type => Bool]

    直交座標データセットの方位角をx方向とy方向のスケールの符号に応じて調整する必要があることを意味します [そのままにしておく]。
  * **U** | **time_stamp** | **timestamp** :: [Type => Str or Bool or []]	$Arg = [[just]/dx/dy/][c|label]$

    プロットにGMTタイムスタンプロゴを描画します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **W** | **pen** :: [Type => Str | Number]

    特定の線の属性を設定します。
  * **X** | **x_offset** | **xshift** :: [Type => Str]     $Arg = [a|c|f|r][x-shift[u]]$
  * **Y** | **y_offset** | **yshift** :: [Type => Str]     $Arg = [a|c|f|r][y-shift[u]]$

    プロットの原点を現在の原点に対して(x-shift,y-shift)だけシフトし、オプションで長さ単位（c, i, またはp）を追加します。
  * **Z** | **azimuth** :: [Type => Bool]

    提供されたthetaグリッドには方向の代わりに方位角が含まれています（-Aを意味します）。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。

完全なドキュメントを見るには、次のコマンドを入力してください: $@? grdvector$ ```
