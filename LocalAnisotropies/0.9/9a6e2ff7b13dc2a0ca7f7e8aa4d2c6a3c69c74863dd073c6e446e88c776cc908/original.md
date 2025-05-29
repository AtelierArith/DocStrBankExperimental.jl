```
to_vtk(vtkfile, coords, localaniso; dir=:ellips, magnitude=:ranges)
```

Export local anisotropies `localaniso` at `coords` to VTK format. It export local ellipsoids by default. If `dir` is set to `:X`, `:Y`, `:Z` or `:XYZ`, local vectors/arrows are exported on these axes. The magnitude can be expressed as `:ranges` (default) or `:ratios`. In the case of `:ratios`, `ratio1=range2/range1` and `ratio2=range3/range1`. Instead of an array of coordinates, `coords` can also be just the georeferenced spatial object. The output `.vtu` file can be loaded in Paraview or similars and processed as Glyphs to plot the directions. If `dir = :ellips`, TensorGlyphs must be used for proper visualization (need to disable extract eigenvalues).
