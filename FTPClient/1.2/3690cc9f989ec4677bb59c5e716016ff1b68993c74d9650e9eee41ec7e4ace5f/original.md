```
ftp_get(
    options::RequestOptions,
    file_name::AbstractString,
    save_path::AbstractString="";
    mode::FTP_MODE=binary_mode,
    verbose::Union{Bool,IOStream}=false,
)
```

Download a file with a non-persistent connection. Returns a `Response`.

# Arguments

  * `options::RequestOptions`: the connection options. See `RequestOptions` for details.
  * `file_name::AbstractString`: the path to the file on the server.
  * `save_path::AbstractString=""`: if not specified the file is written to the `Response`   body.
  * `mode::FTP_MODE=binary_mode`: defines whether the file is transferred in binary or ASCII   format.
  * `verbose::Union{Bool,IOStream}=false`: an `IOStream` to capture LibCurl's output or a   `Bool`, if true output is written to STDERR.
