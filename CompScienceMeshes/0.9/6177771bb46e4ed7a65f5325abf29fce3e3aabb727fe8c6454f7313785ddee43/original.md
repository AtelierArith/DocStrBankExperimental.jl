```
readmesh(filename)
```

Reads a mesh in *in* format from `filename`. The format follows:

```
1
V C
x1_1    x1_2    ... x1_U
x2_1    x2_2    ... x2_U
...
xV_1    xV_2    ... xV_U
i1_1    i1_2    ... i1_D1
i2_1    i2_2    ... i2_D1
...
iC_1    iC_2    ... iC_D1
```

where `U` is the universedimension of the mesh, `D1` the dimension of the mesh plus one, `V` the number of vertices, and `C` the number of cells in the mesh.
