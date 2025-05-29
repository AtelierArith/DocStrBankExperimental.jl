```
read_Gmsh_2D(filename, args...)
```

Reads a 2D triangular Gmsh file. Mesh formats 2.2 and 4.1 supported.  Returns (VX, VY), EToV. 

# Examples

```julia
VXY, EToV = read_Gmsh_2D("eulerSquareCylinder2D.msh") # v2.2 file format
VXY, EToV = read_Gmsh_2D("test/testset_Gmsh_meshes/periodicity_mesh_v4.msh") # v4.1 file format

# if MeshImportOptions.grouping=true, then a third variable `grouping` is returned
VXY, EToV, grouping = read_Gmsh_2D("test/testset_Gmsh_meshes/periodicity_mesh_v4.msh", MeshImportOptions(true, false))
VXY, EToV, grouping = read_Gmsh_2D("test/testset_Gmsh_meshes/periodicity_mesh_v4.msh", true) # same as above
```

# See also

https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format
https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format-version-2-*0028Legacy*0029
