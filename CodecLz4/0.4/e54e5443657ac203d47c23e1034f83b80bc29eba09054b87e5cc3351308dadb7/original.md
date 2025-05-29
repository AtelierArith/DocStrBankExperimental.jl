```
LZ4FrameCompressor(; kwargs...)
```

Creates an LZ4 compression codec.

# Keywords

  * `blocksizeid::BlockSizeID=default_size`: `max64KB`, `max256KB`, `max1MB`, or `max4MB` or `default_size`
  * `blockmode::BlockMode=block_linked`:  `block_linked` or `block_independent`
  * `contentchecksum::Bool=false`: if `true`, frame is terminated with a   32-bits checksum of decompressed data
  * `frametype::FrameType=normal_frame)`:  `normal_frame` or `skippable_frame`
  * `contentsize::Integer=0`: Size of uncompressed content (0 for unknown)
  * `blockchecksum::Bool=false`: if `true`, each block is followed by a   checksum of block's compressed data
  * `compressionlevel::Integer=0`: compression level (-1..12)
  * `autoflush::Bool=false`: always flush if `true`
