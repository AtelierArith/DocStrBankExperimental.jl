```
read_Gmsh_2D_v2(filename)
```

Reads triangular GMSH 2D file format 2.2 0 8. Returns (VX, VY), EToV.

# Examples

```julia
VXY, EToV = read_Gmsh_2D_v2("eulerSquareCylinder2D.msh")
```

https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format-version-2-*0028Legacy*0029
