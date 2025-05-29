```
ZlibDeflateInputStream(input[; <keyword arguments>])
```

Construct a zlib deflate input stream to compress gzip/zlib data.

# Arguments

  * `input`: a byte vector, IO object, or BufferedInputStream containing data to compress.
  * `bufsize::Integer=8192`: input and output buffer size.
  * `raw::Bool=false`: if true, data is raw compress data, without zlib metadata
  * `gzip::Bool=true`: if true, data is gzip compressed; if false, zlib compressed.
  * `level::Integer=6`: compression level in 1-9.
  * `mem_level::Integer=8`: memory to use for compression in 1-9.
  * `strategy=Z_DEFAULT_STRATEGY`: compression strategy; see zlib documentation.
