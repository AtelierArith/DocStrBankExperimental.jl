```
file_size(client::PCloudClient; kwargs...)
```

Gives `size` (in bytes) and current `offset` for a given `fd`.

Source: https://docs.pcloud.com/methods/fileops/file_size.html

# Arguments

  * `fd::Int`: the file descriptor, for which the size and offset are given

# Output Example

```
{
    result: 0,
    size: "Size of the ",
    offset: "Current offset"
}
```
