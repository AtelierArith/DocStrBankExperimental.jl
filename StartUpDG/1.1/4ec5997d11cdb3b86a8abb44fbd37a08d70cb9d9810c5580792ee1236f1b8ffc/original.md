```
function read_Gmsh_2D_v4(filename, options)
```

reads triangular GMSH 2D .msh files.

# Output

This depends on if grouping is opted for or not

  * returns: (VX, VY), EToV
  * returns: (VX, VY), EToV, grouping

# Supported formats and features:

  * version 4.1   'physical group support   'remap group ids

## grouping application

When modeling the wave equation you might want wave speeds to vary across your domain. By assigning physical groups in Gmsh we can maintain such groupings upon importing the .msh file. Each imported element will be a member of a phyical group.

```julia
VXY, EToV = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh")
VXY, EToV = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh",false)
VXY, EToV, grouping = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh", true)

option = MeshImportOption(true)
VXY, EToV, grouping = read_Gmsh_2D_v4("eulerSquareCylinder2D.msh", option)
```

https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format

Notes: the version 4 format has a more detailed block data format this leads to more complicated parser.
