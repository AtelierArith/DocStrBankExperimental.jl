```
upload(
    ftp::FTP,
    local_path_io::IO,
    remote_path::AbstractString;
    ftp_options=ftp.ctxt,
    mode::FTP_MODE=binary_mode,
```

) -> Response

Upload IO object "local*path*io" to the FTP server and save as "remote_path".

# Arguments

  * `ftp::FTP`: The FTP to deliver to. See FTPClient.FTP for details.
  * `local_path_io::IO`: The IO object that we want to deliver.
  * `remote_path::AbstractString`: The path that we want to deliver to.

# Keywords

  * `ftp_options=ftp.ctxt`: FTP Options
  * `mode::FTP_MODE=binary_mode`: Set the ftp mode.

# Returns

`FTPResponse`: Returns the ftp response object
