```julia
struct BlobEntry
```

A `BlobEntry` is a small about of structured data that holds reference information to find an actual blob. Many `BlobEntry`s  can exist on different graph nodes spanning Agents and Factor Graphs which can all reference the same `Blob`.

Notes:

  * `blobId`s should be unique within a blobstore and are immutable.
