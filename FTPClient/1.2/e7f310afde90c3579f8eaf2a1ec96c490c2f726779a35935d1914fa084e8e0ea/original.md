```
upload(
    ftp::FTP,
    local_path::AbstractString,
    remote_path::AbstractString;
    ftp_options=ftp.ctxt,
    mode::FTP_MODE=binary_mode,
) -> Response
```

Uploads the file specified in "local*path" to the file or directory specifies in "remote*path".

If "remote*path" is a path to a file, then the file will be uploaded to the FTP using the provided path. If "remote*path" is a path to a directory (which means it ends in "/", ".", or ".."), then the file will be uploaded to the specified directory but with the "local_path" basename as the file name.

# Arguments

  * `ftp::FTP`: The FTP to deliver to. See FTPClient.FTP for details.
  * `local_path::AbstractString`: The file path to the file we want to deliver.
  * `remote_path::AbstractString`: The file/dir path that we want to deliver to.

# Keywords

  * `ftp_options=ftp.ctxt`: FTP Options
  * `mode::FTP_MODE=binary_mode`: Set the ftp mode.

# Returns

`FTPResponse`: Returns the ftp response object
