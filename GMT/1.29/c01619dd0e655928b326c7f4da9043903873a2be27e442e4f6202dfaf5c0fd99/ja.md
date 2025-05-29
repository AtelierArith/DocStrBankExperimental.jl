```
grdsample(cmd0::String="", arg1=nothing, kwargs...)
```

グリッドファイルを読み込み、異なる登録、または新しいグリッド間隔やノード数、さらには新しいサブリージョンを作成するために補間します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdsample`](http://docs.generic-mapping-tools.org/latest/grdsample.html)を参照してください。

## パラメータ

  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdsample(....)の形式を使用してください。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッド間隔です。オプションで、増分単位を追加します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合は、データの最小バウンディングボックスに設定します。
  * **T** | **toggle** :: [Type => Bool]

    出力グリッドのノード登録を切り替え、入力グリッドの反対になるようにします。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにb、バイキュービック補間のためにc、バイリニア補間のためにl、または最近傍値のためにnを追加してグリッド補間モードを選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノード登録を強制します [デフォルトはグリッドライン登録]。
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    OpenMP対応のマルチスレッドアルゴリズムで使用されるコアの数を制限します。(http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)

完全なドキュメントを見るには、次のように入力してください: $@? grdsample$
