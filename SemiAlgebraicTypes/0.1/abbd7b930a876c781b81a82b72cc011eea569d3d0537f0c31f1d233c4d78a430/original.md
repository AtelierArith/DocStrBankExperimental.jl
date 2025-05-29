```
cc_subdivide!(msh::HMesh, n::Int64 = 1)
```

Catmull-Clark subdivision of a Half-Edge mesh.

The mesh `msh` is replaced by the subdivided mesh, applying n times Catmull-Clark scheme.
