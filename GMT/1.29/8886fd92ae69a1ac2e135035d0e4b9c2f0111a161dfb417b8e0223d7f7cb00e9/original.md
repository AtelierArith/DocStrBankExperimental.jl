```
GI = rasterzones(GI::GItype, shapes::GDtype, fun::Function; touches=false)
```

or

```
GI = rasterzones(fun::Function, GI::GItype, shapes::GDtype; touches=false)
```

Compute the statistics of `fun` applied to the elements of the grid or image `GI` that lie inside the polygons of the GMTdataset `shapes`. See the `rasterzones!` documentation for more details. The difference is that this function returns a new grid/image instead of changing the input.
