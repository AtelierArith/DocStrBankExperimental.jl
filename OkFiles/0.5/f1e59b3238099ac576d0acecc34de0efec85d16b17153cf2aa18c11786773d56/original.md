`filelistall(expr::Regex, sftp::SFTPClient.SFTP, vararg...)`

# Example

Return a list of all files start with string "2024" in the sftp and all its subdirectory, and then download all files in this list:

```julia
using SFTPClient, OkFiles

sftp = SFTP("sftp://123.456.78.90", "myservername", "thisispassword")

download_list = filelistall(r"^2024.*", sftp)

mkpath.(joinpath.("data", "file2024", dirname.(download_list))) # directories of destination should be created otherwise `SFTPClient.download` will fail.

SFTPClient.download.(sftp, download_list, downloadDir="data/file2024")
```

!!! note
    `vararg` must follow the `SFTPClient` interface. For more information, please refer `OkFiles.sftpvararginterface`.


# Example

Search only files in the "em13" folder of the `sftp` server:

```julia
download_list = filelistall(r"^2024.*", sftp, "em13")
```
