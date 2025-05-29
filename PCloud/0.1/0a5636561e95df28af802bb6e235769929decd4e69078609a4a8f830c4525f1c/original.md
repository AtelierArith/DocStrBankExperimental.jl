```
file_open(client::PCloudClient; kwargs...)
```

Opens a file descriptor.

Source: https://docs.pcloud.com/methods/fileops/file_open.html

# Arguments

  * `flags::Int`: which can be a combination of the file_open flags.

# Optional Arguments

  * `path::String`: path to the file, for which the file descirptior is created.
  * `fileid::Int`: id of the folder, for which the file descirptior is created.
  * `folderid::Int`: id of the folder, in which new file is created and file descirptior is returned.
  * `name::String`: name of the file, in which new file is created and file descirptior is returned.

The use of these parameters, depends on the flags are given. Please, see the details below.

# Output

On success returns `fd` file descriptor which can be used in successive operations. Also returns the `fileid` of the file (useful when creating file).

# Output Example

```
{
    result: 0,
    fd: 1,
    fileid: 3489
}
```
