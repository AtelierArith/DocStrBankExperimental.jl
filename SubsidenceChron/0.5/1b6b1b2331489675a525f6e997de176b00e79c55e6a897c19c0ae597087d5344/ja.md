```julia
find_formation_depths(formation, thickness)
```

各ユニークな層の上部と下部の深さを、層序単位と厚さのリストを用いて見つけます。

### 例:

```julia
ds = importdataset(joinpath("..", "examples", "Svalbard_highres.csv"), importas=:Tuple)
formations, tops bottoms = find_formation_depths(ds.Formation, ds.Thickness)
```
