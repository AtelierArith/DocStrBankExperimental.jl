```
ZlibInflateInputStream(input[; <keyword arguments>])
```

Construct a zlib inflate input stream to decompress gzip/zlib data.

# Arguments

  * `input`: a byte vector, IO object, or BufferedInputStream containing compressed data to inflate.
  * `bufsize::Integer=8192`: input and output buffer size.
  * `raw::Bool=falso`: if true, data is raw compress data, without zlib metadata
  * `gzip::Bool=true`: if true, data is gzip compressed; if false, zlib compressed.
  * `reset_on_end::Bool=true`: on stream end, try to find the start of another stream.
