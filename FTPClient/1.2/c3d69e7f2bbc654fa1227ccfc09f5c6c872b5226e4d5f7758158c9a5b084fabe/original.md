```
FTP(; kwargs...) -> FTP
```

Create an FTP object.

# Keywords

  * `hostname::AbstractString=""`: the hostname or address of the FTP server.
  * `username::AbstractString=""`: the username used to access the FTP server.
  * `password::AbstractString=""`: the password used to access the FTP server.
  * `ssl::Bool=false`: use a secure FTP connection.
  * `implicit::Bool=false`: use implicit security (FTPS).
  * `verify_peer::Bool=true`: verify authenticity of peer's certificate.
  * `active_mode::Bool=false`: use active mode to establish data connection.
  * `verbose::Union{Bool,IOStream}=false`: an `IOStream` to capture LibCurl's output or a   `Bool`, if true output is written to STDERR.
