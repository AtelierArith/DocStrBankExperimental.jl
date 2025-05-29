```
file_seek(client::PCloudClient; kwargs...)
```

Sets the current offset of the file descriptor to `offset` bytes.

This methods works in the following modes, depending on the `whence` parameter:

  * `0`: moves after beginning of the file
  * `1`: after current position
  * `2`: after end of the file

Source: https://docs.pcloud.com/methods/fileops/file_seek.html

# Arguments

  * `fd::Int`: the file descriptor, for which the current offset is changed
  * `offset::Int`: the offset in bytes, to which to move the current offset

# Optional Arguments

  * `whence::Int`: mode, in which the offset seek works. Default value is 0

# Output

Returns the new `offset`.

# Output Example

```
{
    result: 0,
    offset: 1024
}
```
