```
Blob(root)
Blob(root, relpath)
```

`Blob` represents the location of a collection of unstructured binary data. The location is a path `relpath` relative to some `root` data resource.

A `Blob` can naturally be `open()`ed as a `Vector{UInt8}`, but can also be mapped into the program as an `IO` byte stream, or interpreted as a `String`.

Blobs can be arranged into hierarchies "directories" via the `BlobTree` type.
