```
Topo_water, sinks, pits, bnds  = waterflows(Topo::GeoData;
    flowdir_fn=WhereTheWaterFlows.d8dir_feature, feedback_fn=nothing, drain_pits=true, bnd_as_sink=true,
    rainfall = nothing,
    minsize=300)
```

Takes a GMG GeoData object of a topographic map and routes water through the grid. Optionally, you can specify `rainfall` in which case we accumulate the rain as specified in this 2D array instead of the cellarea. This allows you to, for example, sum, up water if you have variable rainfall in the area. The other options are as in the `waterflows` function of the package `WhereTheWaterFlows`.

# Example

```julia-repl
# Download some topographic data
julia> Topo = import_topo([6.5,7.3,50.2,50.6], file="@earth_relief_03s");

# Flow the water through the area:
julia> Topo_water, sinks, pits, bnds  = waterflows(Topo)
julia> Topo_water
GeoData
  size      : (961, 481, 1)
  lon       ϵ [ 6.5 : 7.3]
  lat       ϵ [ 50.2 : 50.59999999999999]
  depth     ϵ [ 0.045 : 0.724]
  fields    : (:Topography, :area, :slen, :dir, :nout, :nin, :c)

```
