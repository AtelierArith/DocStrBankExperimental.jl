```
function displace_mesh(xgrid::ExtendableGrid, source::FEVectorBlock; magnify = 1)
```

Returns a new grid by adding the displacement field in source (expects a vector-valued finite element) to the coordinates of the provided xgrid times a magnify value.
