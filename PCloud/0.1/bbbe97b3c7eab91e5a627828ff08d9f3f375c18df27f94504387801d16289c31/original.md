```
file_truncate(client::PCloudClient; kwargs...)
```

Sets file size to `length` bytes.

If `length` is less than the file size, then the extra data is cut from the file, else the the file contents are extended with zeroes as needed.

The current offset is not modified.

Source: https://docs.pcloud.com/methods/fileops/file_truncate.html

# Arguments

  * `fd::Int`: the file descriptor, for which the size and offset are given
  * `length::Int`: to how much bytes to set the file size

# Output Example

```
{
    result: 0
}
```
