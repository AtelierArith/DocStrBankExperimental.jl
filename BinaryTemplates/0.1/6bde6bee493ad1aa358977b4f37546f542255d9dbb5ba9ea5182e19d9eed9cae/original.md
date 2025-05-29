```
HeaderOnlyBinaryTemplate
```

AbstractBinaryTemplate that consists of a single chunk at the beginning of the file.

# Fields

  * `expected_file_size::Int`: Expected size of the file
  * `header::Vector{UInt8}`: Chunk of bytes to be written to the template header
