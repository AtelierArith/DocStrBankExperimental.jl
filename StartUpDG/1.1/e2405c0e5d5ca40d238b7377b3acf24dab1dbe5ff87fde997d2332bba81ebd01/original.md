```
MeshData_to_vtk(md, rd, dim, data, dataname, datatype, filename, write_data = false, equi_dist_nodes = true)
```

Translate the given mesh into a vtk-file. `md` holds a `MeshData` object `rd` holds a reference element data/`RefElemData` object.  `data` holds an array of arrays (of size `num_nodes` by `num_elements`) with plotting data `dataname` is an array of strings with name of the associated data `write_data`, flag if data should be written or not (e.g., if data is not written, only the mesh will be saved as output) `equi_dist_nodes` flag if points should be interpolated to equidstant nodes
