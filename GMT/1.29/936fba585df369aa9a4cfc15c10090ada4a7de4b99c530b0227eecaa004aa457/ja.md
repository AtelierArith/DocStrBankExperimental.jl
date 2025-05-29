```
binstats(cmd0::String="", arg1=nothing; kwargs...)
```

任意の位置にある (x,y[,z][,w]) ポイント (2-4 列) を読み取り、指定されたグリッドレイアウト内の各ノードに対して、与えられた半径内にあるポイントを特定します。これらのポイントは、指定された統計量の計算に使用されます。結果はそのまま表示することも、円の面積で正規化して密度推定を行うこともできます。あるいは、六角形のタイルを選択するか、長方形のグリッドレイアウトを選択することもできます。

## パラメータ

  * **C** | **stats** | **statistic** :: [Type => String | NamedTuple]

    ノードの半径距離内にあるポイントに基づいて計算される統計量を選択します。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッドの間隔です。オプションで、増分単位を追加できます。
  * **E** | **empty** :: [Type => Number]

    空のノードに割り当てられる値を設定します [NaN]。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = gmtbinstats(....) 形式を使用してください。
  * **N** | **normalize** :: [Type => Bool]

    結果のグリッド値を `search_radius` によって表される面積で正規化します。
  * **S** | **search_radius** :: [Type => Number]

    ノードに近いと見なされるデータポイントを決定する search_radius を設定します。`tiling` とは互換性がありません。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **T** | **tiling** | **bins** :: [Type => String | NamedTuple]

    円形の重複する領域の代わりに、重複しないタイルを選択します。長方形または六角形のビニングのいずれかを選択します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告を stderr に送信する冗長性レベルを選択します。
  * **W** | **weights** :: [Type => Bool | String]

    入力データには、観測ポイントの重みを含む 4 番目の列があります。

完全なドキュメントを見るには、次のように入力してください: $@? gmtbinstats$
