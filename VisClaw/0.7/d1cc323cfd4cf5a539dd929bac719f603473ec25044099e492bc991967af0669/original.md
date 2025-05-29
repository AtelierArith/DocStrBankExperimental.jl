```
xyrange = getR(tiles::Vector{VisClaw.AMRGrid}; length_unit="")
xyrange = getR(topo::VisClaw.AbstractTopo; length_unit="")
xyrange = getR(region::VisClaw.Region; length_unit="")
xyrange = getR(G::GMT.GMTgrid; length_unit="")
```

Get x and y ranges in AbstractString for -R option in GMT
