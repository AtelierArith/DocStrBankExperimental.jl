```
filecmp(path1::AbstractString, path2::AbstractString, bufsize=0; info=Val(false); limit=0)
filecmp(io1::IO, io2::IO, bufsize=0; info=Val(false), limit=0)
```

Determine if files at `path1` and `path2` have the same content and optionally return information on how they differ. For `info==false` the return type is `Bool`. In this case, return `true` if files at `path1` and `path2` are equal byte by byte and `false` otherwise.

For `info==true` the return type is `FileCmp.Info`, which records at which byte index, if any, the files differ, and a comparison of the sizes of the files. (See [`FileCmp.Info`](@ref)). The result may be queried by the functions `files_equal`, `got_eof`, and `bytes_read`.

If `path1` or `path2` does not exist an exception is thrown.

The keyword argument `info` may be one of `true`, `false`, `Val(true)`, or `Val(false)`. The first two are more convenient. The latter two allow the return type to be inferred.

If `limit` is greater than zero, then read at most `limit` bytes.

The files are read into buffers of `bufsize` bytes. If `bufsize=0`, then a default is used.

# Examples

Simplest use

```julia
using FileCmp
filecmp("file1", "file2")  # Return `true` or `false`
```

For more information do this

```julia
using FileCmp: filecmp, bytes_read, got_eof, files_equal
info_result = filecmp("file1", "file2"; info=true)
bytes_read(info_result) # how many bytes were read
got_eof(info_result) # Did we get eof on a file ? (see the docstring for got_eof)
files_equal(info_result) # are the files equal ?
```
