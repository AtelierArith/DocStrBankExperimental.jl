```
triangulate(cmd0::String="", arg1=nothing; kwargs...)
```

ランダムに間隔を空けた x,y[,z](またはファイル) を読み込み、デローニ三角形分割を実行します。つまり、点をどのように接続すれば最も正三角形に近い三角形分割が得られるかを見つけます。

完全な GMT (GMT.jl ではない) ドキュメントは [`triangulate`](http://docs.generic-mapping-tools.org/latest/triangulate.html) を参照してください。

## パラメータ

  * **A** | **area** :: [Type => Bool]

    デカルト三角形の面積を計算し、出力セグメントヘッダーに面積を追加します [面積は計算されません]。**triangles** が必要で、**voronoi** とは互換性がありません (GMT >= 6.4)。
  * **C** | **slope_grid** :: [Type => Number]

    勾配グリッド (度単位) を読み込み、CURVE アルゴリズムを使用して水深の伝播不確実性を計算します。
  * **D** | **derivatives** :: [Type => Str]

    平面のファセットで表される表面の x または y の導関数を取得します (G が設定されているときのみ使用されます)。
  * **E** | **empty** :: [Type => Str | Number]

    G が設定されているときに空のノードに割り当てられる値を設定します [NaN]。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    三角形分割を使用してデータを均等なグリッド (R I で指定) にグリッド化します。出力グリッドファイルの名前を追加します。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッド間隔です。オプションで、増分単位を追加します。
  * **J** | **proj** | **projection** :: [Type => String]

    地図の投影を選択します。デフォルトは 15x10 cm の線形 (非投影) 地図です。
  * **L** | **index** :: [Type => Bool]

    以前に計算されたデローニ情報のファイル名を指定します。インデックスファイルがバイナリで、バイナリ入力テーブルと同じ方法で読み取れる場合は、+b を追加して読み取りを高速化できます (GMT6.4)。
  * **M** | **network** :: [Type => Bool]

    三角形分割ネットワークをセグメントヘッダーレコードで区切られた複数の線分として出力します。
  * **N** | **ids** :: [Type => Bool]

    G と組み合わせて使用し、すべてのデローニ頂点の ID の三つ組を出力します。
  * **Q** | **voronoi** :: [Type => Str | []]

    ボロノイセルのエッジを出力します [デフォルトはデローニ三角形のエッジ]。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **triangles** :: [Type => Bool]  

    三角形をセグメントヘッダーレコードで区切られたポリゴンセグメントとして出力します。デローニ三角形分割が必要です。
  * **T** | **edges** :: [Type => Bool]

    G オプションでグリッド化が選択されていてもエッジまたはポリゴンを出力します。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告を stderr に送信する冗長性レベルを選択します。
  * **Z** | **xyz** | **triplets** :: [Type => Bool]
  * **bi** | **binary_in** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    プライマリ入力のネイティブバイナリ形式を選択します (セカンダリ入力は常に ASCII です)。
  * **bo** | **binary_out** :: [Type => Str]			$Arg = [ncols][type][w][+L|+B]$

    ネイティブバイナリ出力を選択します。
  * **di** | **nodata_in** :: [Type => Str or Number]      $Arg = nodata$

    すべての入力列を調べ、任意の項目が nodata と等しい場合、この値を欠損データ項目として解釈し、NaN に置き換えます。
  * **e** | **pattern** | **find** :: [Type => Str]        $Arg = [~]”pattern” | -e[~]/regexp/[i]$

    指定されたパターンを含む ASCII データレコードのみを受け入れます。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型を指定します (時間または地理データ)。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    プライマリ入力ファイルにはヘッダーレコードがあります。
  * **i** | **incols** | **incol** :: [Type => Str]      $Arg = cols[+l][+sscale][+ooffset][,…]$

    プライマリ入力の特定のデータ列を任意の順序で選択します。
  * **r** | **reg** | **registration** :: [Type => Bool or []]

    ピクセルノードの登録を強制します [デフォルトはグリッドライン登録]。
  * **w** | **wrap** | **cyclic** :: [Type => Str or Number]  $Arg = [[-]n]$

    入力レコードを循環座標に変換します。
  * **yx** :: [Type => Str or Bool or []]     $Arg = [i|o]$

    入力および/または出力で 1 番目と 2 番目の列を入れ替えます。

完全なドキュメントを見るには、次のように入力してください: $@? triangulate$
