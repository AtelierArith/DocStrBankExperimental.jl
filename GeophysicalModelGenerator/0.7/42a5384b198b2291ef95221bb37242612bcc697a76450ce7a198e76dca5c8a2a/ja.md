```
Topo_water, sinks, pits, bnds  = waterflows(Topo::GeoData;
    flowdir_fn=WhereTheWaterFlows.d8dir_feature, feedback_fn=nothing, drain_pits=true, bnd_as_sink=true,
    rainfall = nothing,
    minsize=300)
```

GMG GeoDataオブジェクトの地形図を取得し、グリッドを通して水を流します。オプションで`rainfall`を指定することができ、その場合はセル面積の代わりにこの2D配列で指定された雨を蓄積します。これにより、例えば、地域に変動する降雨がある場合に水を合計することができます。他のオプションは、パッケージ`WhereTheWaterFlows`の`waterflows`関数と同様です。

# 例

```julia-repl
# 地形データをダウンロードする
julia> Topo = import_topo([6.5,7.3,50.2,50.6], file="@earth_relief_03s");

# エリアを通して水を流す:
julia> Topo_water, sinks, pits, bnds  = waterflows(Topo)
julia> Topo_water
GeoData
  size      : (961, 481, 1)
  lon       ϵ [ 6.5 : 7.3]
  lat       ϵ [ 50.2 : 50.59999999999999]
  depth     ϵ [ 0.045 : 0.724]
  fields    : (:Topography, :area, :slen, :dir, :nout, :nin, :c)

```
