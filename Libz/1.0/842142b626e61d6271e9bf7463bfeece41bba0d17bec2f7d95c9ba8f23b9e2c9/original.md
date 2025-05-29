```
ZlibInflateOutputStream(output[; <keyword arguments>])
```

Construct a zlib inflate output stream to decompress gzip/zlib data.

# Arguments

  * `output`: a byte vector, IO object, or BufferedInputStream to which decompressed data should be written.
  * `bufsize::Integer=8192`: input and output buffer size.
  * `raw::Bool=false`: if true, data is raw compress data, without zlib metadata
  * `gzip::Bool=true`: if true, data is gzip compressed; if false, zlib compressed.
