```julia
mutable struct TiffFile{O<:Unsigned, S<:FileIO.Stream}
```

-> TiffFile

Wrap `io` with helper parameters to keep track of file attributes.

  * `uuid`: A unique identifier for this file
  * `filepath`: The relative path to this file
  * `io`: The file stream
  * `first_offset`: Location of the first IFD in the file stream
  * `need_bswap`: Whether this file has a different endianness than the host computer
