```
grdfilter(cmd0::String="", arg1=nothing, kwargs...)
```

時間領域でグリッドファイルをフィルタリングし、選択した畳み込みまたは非畳み込みの等方性または長方形フィルタのいずれかを使用して、直交座標系または球面幾何学を使用して距離を計算します。

完全なGMT（`GMT.jl`ではなく）ドキュメントは[`grdfilter`](http://docs.generic-mapping-tools.org/latest/grdfilter.html)を参照してください。

## パラメータ

  * **F** | **filter** :: [Type => Str]

    フィルタタイプを設定します。
  * **D** | **distflag** | **distance** :: [Type => Number]

    距離フラグは、グリッド（x,y）がフィルタ幅にどのように関連するかを示します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdfilter(....)の形式を使用してください。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで*y_inc*]はグリッド間隔です。オプションで、増分単位を追加します。
  * **N** | **nans** :: [Type => Str]

    入力グリッドのNaN値がフィルタリングされた出力にどのように影響するかを決定します。値はi|p|rです。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合は、データの最小バウンディングボックスに設定します。
  * **T** | **toggle** :: [Type => Bool]

    出力グリッドのノード登録を切り替えて、入力グリッドの反対になるようにします。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。

完全なドキュメントを見るには、次のように入力してください: $@? grdfilter$
