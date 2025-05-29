```julia
mutable struct QPInfos{Ti, Tv, Ttime, Tx, Txref, TvG, TiG, PT}
```

object that shares information about the current quadrature point (item number w.r.t. current AssemblyType, cell number when reasonable, region number w.r.t. current AssemblyType, volume if the item, normal when reasonable, current time, current world coordinates, current reference coordinates, set of parameters)
