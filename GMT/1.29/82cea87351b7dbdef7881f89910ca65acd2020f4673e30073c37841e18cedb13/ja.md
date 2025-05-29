```
grdlandmask([monolithic::String="";] area=, resolution=, bordervalues=, save=, maskvalues=, registration=, verbose=, cores=)
```

土地と水のために設定された値を持つグリッドファイルを作成します。

選択した海岸線データベースを読み込み、指定されたグリッド内のどのノードが陸上または水上であるかを指定するグリッドを作成します。選択された地域と格子間隔によって定義されたノードは、次の2つの基準のいずれかに従って設定されます：(1) 陸上対水上、または (2) より詳細な（階層的な）海洋対陸上対湖対島対池。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdlandmask`](http://docs.generic-mapping-tools.org/latest/grdlandmask.html)を参照してください。

## パラメータ

  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある地域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッド間隔です。オプションで、増分単位を追加できます。
  * **A** | **area** :: [Type => Str | Number]

    面積がmin*area km^2未満の特徴や、階層レベルがmin*levelより低いかmax_levelより高いものはプロットされません。
  * **D** | **res** | **resolution** :: [Type => Str]

    使用するデータセットの解像度を選択します（(f)ull, (h)igh, (i)ntermediate, (l)ow, および (c)rude）。
  * **E** | **border** | **bordervalues** :: [Type => Str | List]    $Arg = cborder/lborder/iborder/pborder or bordervalue$

    ポリゴン境界上に正確に落ちるノードはポリゴンの外側にあると見なされるべきです [デフォルトでは内部と見なされます]。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdlandmask(....)形式を使用してください。
  * **N** | **maskvalues** | **mask** :: [Type => Str | List]    $Arg = wet/dry or ocean/land/lake/island/pond$

    ノードに割り当てられる値を設定します。値は任意の数値、NaNというテキスト文字列を含むことができます。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    OpenMP対応のマルチスレッドアルゴリズムで使用されるコアの数を制限します。(http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)

完全なドキュメントを見るには、次のように入力してください: $@? grdlandmask$
