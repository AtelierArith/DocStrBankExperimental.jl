```
findtiles(ni::Int,nj::Int,mygrid::gcmgrid)
findtiles(ni::Int,nj::Int,grid::String="LatLonCap",GridParentDir="../inputs/GRID_LLC90/")
```

Return a `MeshArray` map of tile indices, `mytiles["tileNo"]`, for tile size `ni,nj` and extract grid variables accordingly.
