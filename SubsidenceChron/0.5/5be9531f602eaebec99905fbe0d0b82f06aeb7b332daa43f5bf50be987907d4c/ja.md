```julia
find_formation_heights(formation, thickness)
```

各ユニークな地層の上部と下部の高さを、地層単位と厚さのリストを用いて見つけます。

### 例:

```julia
ds = importdataset(joinpath("..", "examples", "Svalbard_highres.csv"), importas=:Tuple)
formations, tops bottoms = find_formation_heights(ds.Formation, ds.Thickness)
```
