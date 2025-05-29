```
function displace_mesh!(xgrid::ExtendableGrid, source::FEVectorBlock; magnify = 1)
```

Moves all nodes of the grid by adding the displacement field in source (expects a vector-valued finite element) times a magnify value.
