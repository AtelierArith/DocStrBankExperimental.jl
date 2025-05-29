```
file_pread(client::PCloudClient; kwargs...)
```

Tries to read at most `count` bytes at the given `offset` of the file.

You can see how to read data here.

Source: https://docs.pcloud.com/methods/fileops/file_pread.html

# Arguments

  * `fd::Int`: the file descriptor, from which data is read
  * `count::Int`: count in bytes, which to be read from the descriptor
  * `offset::Int`: in bytes, from where to start reading in the file

# Output

Returns the data.
