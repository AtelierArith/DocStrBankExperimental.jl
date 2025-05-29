```
file_write(client::PCloudClient; kwargs...)
```

Writes as much data as you send to the file descriptor `fd` to the current file offset and adjusts the offset.

You can see how to send data here.

Source: https://docs.pcloud.com/methods/fileops/file_write.html

# Arguments

  * `fd::Int`: the file descriptor, to which data is written

# Output

Returns `bytes` (number of bytes) written.

# Output Example

```
{
    result: 0,
    bytes: 124
}
```
