```
ftp_put(
    ctxt::ConnContext,
    file_name::AbstractString,
    file::IO;
    mode::FTP_MODE=binary_mode,
)
```

Upload file with persistent connection. Returns a `Response`.

# Arguments

  * `ctxt::ConnContext`: encompases the connection options defined via ftp_connect. See   `RequestOptions` for details.
  * `file_name::AbstractString`: the path to the file on the server.
  * `file::IO`: what is being written to the server.
  * `mode::FTP_MODE=binary_mode`: defines whether the file is transferred in binary or   ASCII format.
