```
export_grid(grid::VoronoiGrid, filename::String, vars::Symbol...)
```

Export grid to a vtk file. Append datasets specified by `vars`. Currently only numbers and vectors can be exported.
