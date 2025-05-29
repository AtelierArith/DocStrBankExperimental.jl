```
gzi(io::IO)
```

Construct a `Vector{UInt8}` with the GZI of a BGZF file of an `IO` representing a BGZF file. GZI files contain offsets for each block and its decompressed payload in a BGZF file. A GZI file is approximately 1/4000th the size of the decompressed data in a BGZF file.

## Examples

```julia
julia open(gzi, "/my/bgzip/file.bgz")
102744-element Array{UInt8,1}:
 0x15
 0x19
 0x00
 0x00
 0x00
[ ... ]
```
