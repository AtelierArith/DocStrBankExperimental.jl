```
gravmag3d(cmd0::String=""; kwargs...)
```

3-D 体の重力/磁気異常を岡部法で計算します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gmtgravmag3d`](http://docs.generic-mapping-tools.org/latest/supplements/potential/gmtgravmag3d.html)を参照してください。

## パラメータ

  * **C** | **density** :: [Type => Str | GMTgrid]

    SI単位での体の密度を設定します。定数密度または変動する密度のグリッドを提供してください。
  * **F** | **track** :: [Type => Str | Matrix | GMTdataset]

    異常が計算される場所を提供します。このオプションは`outgrid`と相互排他的です。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = gmtgravmag3d(....)の形式を使用してください。
  * **H** | **mag_params** :: [Type => Number]

    磁気異常の計算のためのパラメータを設定します。代わりに、磁気強度グリッドを提供してください。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで*y_inc*]はグリッド間隔です。オプションで、増分単位を追加できます。
  * **L** | **z_obs** | **observation_level** :: [Type => Number]

    観測レベルを設定します [デフォルト = 0]。これは異常が計算される高さ（z）です。
  * **M** | **body** :: [Type => Str | Tuple]

    幾何学的な体を作成し、その重力/磁気効果を計算します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定されます。
  * **S** | **radius** :: [Type => Number]

    検索半径をkm単位で設定します（2つのグリッドモードまたは`thickness`のときのみ有効）[デフォルト = 30 km]。
  * **T+v** | **index** :: [Type => Str]
  * **T+r** | **raw_triang** :: [Type => Str]
  * **T+s** | **stl** :: [Type => Str]

    閉じた表面を定義するxyzおよび頂点（ndex="vert_file"）ファイルの名前を提供します。
  * **Z** | **level** | **reference_level** :: [Type => Number]

    参照平面のレベル [デフォルト = 0]。

### 例

```julia
	G = gmtgravmag3d(M=(shape=:prism, params=(1,1,1,5)), inc=1.0, region="-15/15/-15/15", mag_params="10/60/10/-10/40");
	imshow(G)
```
