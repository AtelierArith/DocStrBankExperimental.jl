```
ZeroTemplate
```

AbstractBinaryTemplate where all the chunks consist bytes equal to `0x00`.

# Fields

  * `expected_file_size::Int`: Expected size of the file
  * `offsets::Vector{Int}`: Byte offsets for each chunk
  * `chunks_lengths::Vector{Int}`: Length of each chunk
