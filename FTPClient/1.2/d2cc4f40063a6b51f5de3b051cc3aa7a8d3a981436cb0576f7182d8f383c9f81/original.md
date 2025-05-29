```
ftp_put(
    options::RequestOptions,
    file_name::AbstractString,
    file::IO;
    mode::FTP_MODE=binary_mode,
    verbose::Union{Bool,IOStream}=false,
)
```

Upload file with non-persistent connection. Returns a Response.

# Arguments

  * `options::RequestOptions`: the connection options. See `RequestOptions` for details.
  * `file_name::AbstractString`: the path to the file on the server.
  * `file::IO`: what is being written to the server.
  * `mode::FTP_MODE=binary_mode`: defines whether the file is transferred in binary or   ASCII format.
  * `verbose::Union{Bool,IOStream}=false`: an `IOStream` to capture LibCurl's output or a   `Bool`, if true output is written to STDERR.
