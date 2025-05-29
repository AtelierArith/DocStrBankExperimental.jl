```
BinaryTemplate
```

General binary template with multiple chunks at various file offsets.

# Fields

  * `expected_file_size::Int`: Expected size of the file
  * `offsets::Vector{Int}`: Byte offsets for each chunk
  * `chunks::Vector{Vector{UInt8}}`: Bytes for each chunk
