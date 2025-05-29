```
barycentric refinement(mesh) -> refined_mesh
```

Create the mesh obtained by inserting an extra vertex in the barycenters of all cells and recusively creating fine cells by connecting the barycenter of a k-cell to the already constructed refined (k-1)-cells on its boundary.
