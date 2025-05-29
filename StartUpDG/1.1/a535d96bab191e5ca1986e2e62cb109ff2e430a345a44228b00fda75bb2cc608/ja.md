```
read_Gmsh_2D_v2(filename)
```

三角形GMSH 2Dファイルフォーマット2.2 0 8を読み込みます。 (VX, VY), EToVを返します。

# 例

```julia
VXY, EToV = read_Gmsh_2D_v2("eulerSquareCylinder2D.msh")
```

https://gmsh.info/doc/texinfo/gmsh.html#MSH-file-format-version-2-*0028Legacy*0029
