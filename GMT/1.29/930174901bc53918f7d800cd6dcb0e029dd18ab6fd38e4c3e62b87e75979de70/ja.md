```
grdblend(cmd0::String="", arg1=nothing, arg2=nothing, kwargs...)
```

グリッドファイルとブレンドパラメータのリストを読み込み、最大2つのGTMgridタイプをブレンドして、コサインテーパー重みを使用してグリッドを作成します。

完全なGMT（`GMT.jl`ではなく）ドキュメントは[`grdblend`](http://docs.generic-mapping-tools.org/latest/grdblend.html)を参照してください。

## パラメータ

  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで*y_inc*]はグリッドの間隔です。オプションで、増分単位を追加します。   (http://docs.generic-mapping-tools.org/latest/grdblend.html#i)
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合にのみ使用されます。それ以外の場合は、G = grdblend(....)の形式を使用してください。
  * **C** | **clobber** :: [Type => Str | []]      $Arg = f|l|o|u[±]$

    クラッシャーモード：ブレンドする代わりに、ノードをカバーするグリッドの1つの値を単に選択します。
  * **N** | **nodata** :: [Type => Str | Number]

    データなし。入力グリッドがないノードにこの値を設定します [デフォルトはNaN]。
  * **Q** | **headless** :: [Type => Bool]

    プレーンなヘッダーなしのグリッドファイルを作成します（外部ツールで使用）。出力グリッドファイルがネイティブ形式である必要があります（すなわち、netCDFではない）。**G**と一緒に使用しないでください。
  * **W** | **no_blend** :: [Type => Str | []]

    ブレンドせず、各ノードに使用される重みを出力します [デフォルトはブレンドを作成します]。$z$を追加して、重み*zの合計を代わりに書き込みます。
  * **Z** | **scale** :: [Type => Number]

    ファイルに書き込む前に出力値をスケールでスケーリングします。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータタイプを指定します（時間または地理データ）。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにb、バイキュービック補間のためにc、バイリニア補間のためにl、または最近傍値のためにnを追加して、グリッド補間モードを選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
