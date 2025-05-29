```
file_pwrite(client::PCloudClient; kwargs...)
```

Writes as much data as you send to the file descriptor `fd`. Data is written at the `offset` that is provided as parameter.

file*pwrite ignores the O*APPEND flag. The file's offset is not changed.

You can see how to send data here.

Source: https://docs.pcloud.com/methods/fileops/file_pwrite.html

# Arguments

  * `fd::Int`: the file descriptor, to which data is written
  * `offset::Int`: the offset in bytes, from where the data is written

# Output

Returns `bytes` (number of bytes) written.

# Output Example

```
{
    result: 0,
    bytes: 124
}
```
