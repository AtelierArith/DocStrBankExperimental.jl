```
numvertices(mesh)
```

Returns the number of vertices in the mesh.

*Note*: this is the number of vertices in the vertex buffer and might include floatin vertices or vertices not appearing in any cell. In other words the following is not necessarily true:

```julia
    numvertices(mesh) == numcells(skeleton(mesh,0))
```
