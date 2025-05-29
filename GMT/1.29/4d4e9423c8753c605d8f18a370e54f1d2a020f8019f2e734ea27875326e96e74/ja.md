```
grdrotater(cmd0::String="", arg1=nothing; kwargs...)
```

地理グリッドを取得し、全体の再構築回転を考慮して再構築します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdrotater`](http://docs.generic-mapping-tools.org/latest/supplements/spotter/grdrotater.html)で確認できます。

## パラメータ

  * **A** | **rot_region** :: [Type => Str | Tuple | Vec]

    回転したグリッドの領域を直接指定します。
  * **D** | **rot_outline** :: [Type => Bool or Str]	$Arg = true | filename$

    グリッドポリゴンアウトラインファイルの名前。これは、指定された時間に再構築されたグリッドのアウトラインを表します。
  * **F** | **rot_polyg** | **rot_polygon** :: [Type => Str | GMTdaset | Mx2 array]	$Arg = filename | dataset)$

    回転すべきグリッドの内部領域を説明する多セグメントの閉じたポリゴンファイルを指定します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdrotater(....)の形式を使用してください。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **T** | **ages** :: [Type => Str | Tuple]

    希望する再構築時間を設定します。単一の時間の場合は、希望する時間を追加します。(http://docs.generic-mapping-tools.org/latest/grdrotater.html#t)
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **b** | **binary** :: [Type => Str]
  * **d** | **nodata** :: [Type => Str or Number]		$Arg = [i|o]nodata$

    ユーザーがコーディングした欠損データ値がGMTの公式NaN値にどのように変換されるかを制御します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **g** | **gap** :: [Type => Str]           $Arg = [a]x|y|d|X|Y|D|[col]z[+|-]gap[u]$

    連続データポイント間の間隔を調べて、線にブレークを課すようにします。
  * **h** | **header** :: [Type => Str]        $Arg = [i|o][n][+c][+d][+rremark][+ttitle]$

    主な入力ファイルにヘッダーレコードがあります。
  * **n** | **interp** | **interpolation** :: [Type => Str]         $Arg = [b|c|l|n][+a][+bBC][+c][+tthreshold]$

    Bスプラインスムージングのためにbを追加するか、バイキュービック補間のためにcを追加するか、バイリニア補間のためにlを追加するか、最近傍値のためにnを追加して、グリッド補間モードを選択します。
  * **o** | **outcols** | **outcol** :: [Type => Str]     $Arg = cols[,…]$

    任意の順序で主な出力の特定のデータ列を選択します。

### 例

```julia
G = grdmath("-R-5/5/-5/5 -I0.1 -fg X Y HYPOT");
tri = [-2.411 -1.629; -0.124 2.601; 2.201 -1.629; -2.410 -1.629];
Gr, tri_rot = grdrotater(G, rotation="-40.8/32.8/-12.9", rot_outline=true, rot_polygon=tri);
imshow(Gr, plot=(data=tri_rot,))
```
