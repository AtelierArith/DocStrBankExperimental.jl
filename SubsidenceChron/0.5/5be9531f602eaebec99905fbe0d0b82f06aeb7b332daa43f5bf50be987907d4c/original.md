```julia
find_formation_heights(formation, thickness)
```

Find the top and bottom height of each unique formation given a list of stratigraphic units and thicknesses

### Examples:

```julia
ds = importdataset(joinpath("..", "examples", "Svalbard_highres.csv"), importas=:Tuple)
formations, tops bottoms = find_formation_heights(ds.Formation, ds.Thickness)
```
