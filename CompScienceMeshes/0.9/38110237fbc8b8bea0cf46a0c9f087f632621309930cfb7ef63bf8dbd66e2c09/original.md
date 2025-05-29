```
weld(mesh1, mesh2, ...;boundary=false) -> welded_mesh
```

Build a mesh by welding or pasting together the inputs. Vertices from different meshes that coincide up to the tolerance will be merged into one. The order cells appear in the output mesh is equal to the order in the inputs. boundary = true; will merge only vertices of different meshes if one of them exists on the 'open' boundary of the mesh.
