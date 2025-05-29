```
file_read(client::PCloudClient; kwargs...)
```

Tries to read at most `count` bytes at the current offset of the file.

If currentofset+count<=filesize this method will satisfy the request and read `count` bytes, otherwise it will return just the bytes available (this is the only way to discover the EOF condition).

You can see how to read data here.

Source: https://docs.pcloud.com/methods/fileops/file_read.html

# Arguments

  * `fd::Int`: the file descriptor, from which data is read
  * `count::Int`: count in bytes, which to be read from the descriptor

# Output

Returns the data.
