```
ChunkIndex{N}
```

This can be used in indexing operations when one wants to  extract a full data chunk from a DiskArray. 

Useful for iterating over chunks of data. 

`d[ChunkIndex(1, 1)]` will extract the first chunk of a 2D-DiskArray
