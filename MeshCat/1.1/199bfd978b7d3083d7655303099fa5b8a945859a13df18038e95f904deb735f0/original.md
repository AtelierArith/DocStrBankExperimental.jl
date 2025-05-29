A MeshFileObject is similar to a MeshFileGeometry, but rather than representing a single geometry, it supports loading an entire object (with geometries, materials, and textures), or even a collection of objects (for supported file types).

Supported formats:     * .obj     * .dae (Collada)

Since mesh files may include references to other files (such as texture images), the MeshFileObject also includes a `resources` dictionary mapping relative paths (as specified in the mesh file) to the contents of the referenced files. Those contents are specified using data URIs, e.g.:

```
data:image/png;base64,<base-64 encoded data here>
```

If you construct a MeshFileObject from a `.dae` or `.obj` file, the resources dictionary will automatically be populated.
