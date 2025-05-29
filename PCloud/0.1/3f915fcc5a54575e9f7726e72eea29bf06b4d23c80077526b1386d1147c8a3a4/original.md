```
file_checksum(client::PCloudClient; kwargs...)
```

Calculates checksums of `count` bytes at `offset` from the file descripor `fd`.

DO NOT use this function to calculate checksums of an entire, unmodified file, use checksumfile instead.

Source: https://docs.pcloud.com/methods/fileops/file_checksum.html

# Arguments

  * `fd::Int`: the file descriptor, for which checksums are calculated
  * `count::Int`: count in bytes, for which checksums are calculated
  * `offset::Int`: from where in bytes the checksum calculation starts

# Output

Returns `sha1`, `md5` and `size`.

`size` will be equal to `count` unless bytes past current filesize are requested to be checksummed.

# Output Example

```
{
    result: 0,
    sha1: "SHA-1 checksum",
    md5: "MD5 checksum",
    size: "count of bytes, for which the checksums are calculated"
}
```
