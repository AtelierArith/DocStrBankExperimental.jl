```
gravprisms(cmd0::String="", arg1=nothing; kwargs...)
```

3次元体の重力/磁気異常を岡部法で計算します。

完全なGMT（`GMT.jl`ではない）ドキュメントは[`gravprisms`](http://docs.generic-mapping-tools.org/latest/supplements/potential/gravprisms.html)を参照してください。

## パラメータ

  * **A** | **zup** :: [Type => Bool]

    z軸は上向きに正であるべきです [デフォルトは下向き]。
  * **D** | **density** :: [Type => Str | GMTgrid]

    SI単位での体密度を設定します。定数密度または変動する密度のグリッドのいずれかを提供します。
  * **E** | **dxdy** | **xy_sides** :: [Type => Number | Tuple numbers]

    テーブル内のすべてのプリズムが一定のx/y寸法を持つ場合、ここで設定できます。その場合、テーブルには各プリズムの中心とz範囲のみを含める必要があります。
  * **F** | **component** :: [Type => Str]

    希望する重力場成分を指定します。
  * **G** | **save** | **outgrid** | **outfile** :: [Type => Str]

    出力グリッドファイル名。これはオプションであり、結果を直接ディスクに保存する場合のみ使用されます。それ以外の場合は、G = gravprisms(....)の形式を使用してください。
  * **H** | **radial_rho** :: [Type => Str | Tuple]

    深さに応じたアドホックな変動半径密度関数のための基準海山パラメータを設定します。
  * **I** | **inc** | **increment** | **spacing** :: [Type => Str]	$Arg = xinc[unit][+e|n][/yinc[unit][+e|n]]]$

    *x_inc* [およびオプションで *y_inc*] はグリッド間隔です。オプションで、増分単位を追加します。
  * **L** | **base** :: [Type => Number ! Grid]

    プリズムで近似したい層の基底面グリッドの名前を指定するか、定数zレベル[0]を指定します。
  * **M** | **units** :: [Type => Str]

    使用する距離単位を設定します。units=:horizontalは、両方の水平距離がkm [m]であることを示します。
  * **N** | **track** :: [Type => Str | Matrix | GMTdataset]

    予測値を計算したい個々の(x, y[, z])位置を指定します。
  * **R** | **region** | **limits** :: [Type => Str or list or GMTgrid|image]	$Arg = (xmin,xmax,ymin,ymax)$

    興味のある領域を指定します。提供されていない場合はデータの最小バウンディングボックスに設定します。
  * **S** | **topography** :: [Type => Number]

    プリズムを作成するための完全な海山の高さを持つグリッドの名前を指定するか、Hによって要求されるものを指定します。
  * **T** | **top** :: [Type => Number | Grid]

    プリズムで近似したい層の上面グリッドの名前を指定するか、定数zレベルを指定します。
  * **Z** | **z_obs** | **observation_level** :: [Type => Number | Grid]

    観測レベルを設定します。定数または観測レベルのグリッドの名前を指定することで変動させることができます。
  * **T** | **top** :: [Type => Number | Grid]

    プリズムで近似したい層の上面グリッドの名前を指定するか、定数zレベルを指定します。
  * **W** | **out*mean*rho** :: [Type => Str]

    CとHによって作成された空間的に変動する、垂直平均のプリズム密度を持つ出力グリッドの名前を指定します。

```
