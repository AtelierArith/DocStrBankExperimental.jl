```julia
find_formation_depths(formation, thickness)
```

Find the top and bottom depth of each unique formation given a list of stratigraphic units and thicknesses

### Examples:

```julia
ds = importdataset(joinpath("..", "examples", "Svalbard_highres.csv"), importas=:Tuple)
formations, tops bottoms = find_formation_depths(ds.Formation, ds.Thickness)
```
