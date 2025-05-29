```
FEData{dim, points_per_cell}
```

Structure that holds Finite Element info with vertex and cell data. Works in 2D/3D for arbitrary elements

# Parameters

  * `vertices` with the points on the mesh (`dim` x `Npoints`)
  * `connectivity` with the connectivity of the mesh (`points_per_cell` x `Ncells`)
  * `fields` with the fields on the vertices
  * `cellfields` with the fields of the cells
