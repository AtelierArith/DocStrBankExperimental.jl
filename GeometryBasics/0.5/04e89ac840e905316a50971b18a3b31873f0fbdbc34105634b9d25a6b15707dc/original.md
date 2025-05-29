```
per_face(data, faces)
per_face(data, mesh)
```

Generates a `FaceView` that applies the given data per face, rather than per vertex. The result can then be used to create a (new) mesh:

```
mesh(..., attribute_name = per_face(data, faces))
mesh(old_mesh, attribute_name = per_face(data, old_mesh))
```
