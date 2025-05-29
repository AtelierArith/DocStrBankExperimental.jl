```
ovf2vtk(ovf_name, vtk_name=nothing; point_data=false, box=noting)
```

Convert ovf file to vtk format. The data will be saved to points if point_data == true otherwise the data will be saved to cells.

If box is not nothing, it should be a tuple. For instance, box = (nx1, nx2, ny1, ny2, nz1, nz2). In this case, the generated vtk only contains the spins inside the box (including the boundary).

```julia
    ovf2vtk("my.ovf", "test.vts")
    ovf2vtk("my.ovf", point_data=true)
```
