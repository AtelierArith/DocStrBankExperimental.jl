```
MultiHash
```

Allows dealing with hashes that self-identify their algorithm, e.g. `sha256:xxxxxxx`. Some pieces of BinaryBuilder, such as an ArchiveSource, may support multiple different hash algorithms. Others, such as a GitSource, currently only support a SHA1Hash, for instance.
