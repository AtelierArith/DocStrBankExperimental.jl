```
egrid = read_egrid(pth)
egrid, raw_egrid = read_egrid(pth, extra_out = true)
```

Read the EGRID file from `pth`. The results are given as a Dict and can be passed further on to `mesh_from_grid_section` to construct a Jutul mesh.

# Notes

This function requires the `resdata` Python package to be installed, which will be automatically added to your environment if you first install PythonCall and put `using PythonCall` in your script or REPL.

Uses primarily `resdata.grid.Grid`.
