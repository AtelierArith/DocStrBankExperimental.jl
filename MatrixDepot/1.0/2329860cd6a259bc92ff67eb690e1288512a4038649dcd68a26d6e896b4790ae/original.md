```
mdopen([db,] pattern)
mdopen(f, [db,] pattern)
```

Return `MatrixDescriptor` object, which can be used with data access functions.

Make sure that data files are loaded. Keeps a cache of already delivered matrices and metadata. If the pattern has not a unique resolution, an error is thrown.
