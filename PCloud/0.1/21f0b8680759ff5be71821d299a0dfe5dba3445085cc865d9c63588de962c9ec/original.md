```
file_pread_ifmod(client::PCloudClient; kwargs...)
```

Same as file_pread, but additionally expects `sha1` or `md5` parameter (hex).

If the checksum of the data to be read matches the `sha1` or `md5` checksum, it returns error code 6000 Not modified.

This call is useful if the application has the data cached and wants to verify if it still current.

You can see how to read data here.

Source: https://docs.pcloud.com/methods/fileops/file*pread*ifmod.html

# Arguments

  * `fd::Int`: the file descriptor, from which data is read
  * `count::Int`: count in bytes, which to be read from the descriptor
  * `offset::Int`: in bytes, from where to start reading in the file
  * `sha1::String`: the SHA-1 checksum of the part of the file from the offset, to be checked
  * `md5::String`: the MD5 checksum of the part of the file from the offset, to be checked

Use `sha1` or `md5`, but not both.

# Output

Returns the data.
