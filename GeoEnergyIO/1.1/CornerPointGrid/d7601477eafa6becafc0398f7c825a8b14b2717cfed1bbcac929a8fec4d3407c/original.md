```
mesh_from_grid_section(f, actnum = missing, repair_zcorn = true, process_pinch = false)
```

Generate a Jutul unstructured mesh from a grid section. The input arugment `f` can be one of the following:

  * (1) An already parsed complete data file read using `parse_data_file`. The "GRID" field will be used.
  * (2) A parsed "GRID" section from `parse_grdecl_file`.
  * (3) The file-name of a `.GRDECL` file to be parsed before processing.

Optionally the `actnum` can be specified separately. The `actnum` should have equal length to the number of logical cells in the grid with true/false indicating if a cell is to be included in the processed mesh.

The additional argument `repair_zcorn` only applies when the grid is defined using COORD/ZCORN arrays. If set to `true`, the monotonicity of the ZCORN coordinates in each corner-point pillar will be checked and optionally fixed prior to mesh construction. Note that if non-monotone ZCORN are fixed, if the first input argument to this function is an already parsed data structure, the ZCORN array will be mutated during fixing to avoid a copy.
