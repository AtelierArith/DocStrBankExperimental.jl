```
findtiles(ni::Int,nj::Int,mygrid::gcmgrid)
findtiles(ni::Int,nj::Int,grid::String="LatLonCap",GridParentDir="../inputs/GRID_LLC90/")
```

タイルサイズ `ni,nj` に対して、タイルインデックスの `MeshArray` マップ `mytiles["tileNo"]` を返し、グリッド変数を適切に抽出します。
