```
ftp_get(
    ctxt::ConnContext,
    file_name::AbstractString,
    save_path::AbstractString="";
    mode::FTP_MODE=binary_mode,
)
```

Download a file with a persistent connection. Returns a `Response`.

# Arguments

  * `ctxt::ConnContext`: encompasses the connection options defined via ftp_connect. See   `RequestOptions` for details.
  * `file_name::AbstractString`: the path to the file on the server.
  * `save_path::AbstractString=""`: if not specified the file is written to the `Response`   body.
  * `mode::FTP_MODE=binary_mode`: defines whether the file is transferred in binary or   ASCII format.
