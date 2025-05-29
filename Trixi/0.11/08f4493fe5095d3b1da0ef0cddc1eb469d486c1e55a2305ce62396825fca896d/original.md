```
UnstructuredMesh2D <: AbstractMesh{2}
```

An unstructured (possibly curved) quadrilateral mesh.

```
UnstructuredMesh2D(filename; RealT=Float64, periodicity=false)
```

All mesh information, neighbour coupling, and boundary curve information is read in from a mesh file `filename`.
