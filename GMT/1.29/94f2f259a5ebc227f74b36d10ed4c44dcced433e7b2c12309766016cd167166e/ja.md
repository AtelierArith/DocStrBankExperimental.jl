```
grdgravmag3d(cmd0::String="", arg1=nothing, arg2=nothing; kwargs...)
```

体積の重力/磁気異常を、1つのグリッドによって提供される表面と平面の間、または2つのグリッドによって提供される上面と下面の間で計算します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`grdgravmag3d`](http://docs.generic-mapping-tools.org/latest/supplements/potential/grdgravmag3d.html)を参照してください。

## パラメータ

  * **C** | **density** :: [Type => Str | GMTgrid]

    SI単位での体密度を設定します。定数密度または変動する密度のグリッドのいずれかを提供します。
  * **F** | **track** :: [Type => Str | Matrix | GMTdataset]

    異常が計算される位置を提供します。このオプションは`outgrid`と相互排他的です。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = grdgravmag3d(....)の形式を使用してください。
  * **E** | **thickness** :: [Type => Number]

    層の厚さをm単位で提供します [デフォルト = 500 m]。
  * **H** | **mag_params** :: [Type => Number]

    磁気異常の計算のためのパラメータを設定します。代わりに、磁気強度グリッドを提供します。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで*y_inc*]はグリッド間隔です。オプションで、増分単位を追加します。
  * **L** | **z_obs** | **observation_level** :: [Type => Number]

    観測レベルを設定します [デフォルト = 0]。これは異常が計算される高さ（z）です。
  * **Q** | **pad** :: [Type => Number]

    出力`region`に関して計算のドメインを拡張します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **radius** :: [Type => Number]

    検索半径をkm単位で設定します（2つのグリッドモードまたは`thickness`のときのみ有効） [デフォルト = 30 km]。
  * **Z** | **level** | **reference_level** :: [Type => Number]

    参照平面のレベル [デフォルト = 0]。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進捗報告をstderrに送信する冗長性レベルを選択します。
  * **f** | **geog** | **colinfo** | **coltypes** | **coltype** :: [Type => Str]        $Arg = [i|o]colinfo$

    入力および/または出力列のデータ型（時間または地理データ）を指定します。
  * **x** | **cores** | **n_threads** :: [Type => Str or Number]  $Arg = [[-]n]$

    OpenMP対応のマルチスレッドアルゴリズムで使用されるコアの数を制限します。   (http://docs.generic-mapping-tools.org/latest/gmt.html#x-full)

### 例. ゴリンジバンクの重力効果を計算します。

```julia
	G = grdgravmag3d("@earth_relief_10m", region=(-12.5,-10,35.5,37.5), density=2700, inc=0.05, pad=0.5, z_level=:bottom, f=:g);
	imshow(G)
```
