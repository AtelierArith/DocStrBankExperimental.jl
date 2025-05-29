```
MetaMesh(mesh; metadata...)
MetaMesh(positions, faces; metadata...)
```

Constructs a MetaMesh either from another `mesh` or by constructing another mesh with the given `positions` and `faces`. Any keyword arguments given will be stored in the `meta` field in `MetaMesh`.

This struct is meant to be used for storage of non-vertex data. Any vertex related data should be stored as a vertex attribute in `Mesh`. One example of such data is material data, which is defined per view in `mesh.views`, i.e. per submesh.

The metadata added to the MetaMesh can be manipulated with Dict-like operations (getindex, setindex!, get, delete, keys, etc). Vertex attributes can be accessed via fields and the same getters as mesh. The mesh itself can be retrieved with `Mesh(metamesh)`.
