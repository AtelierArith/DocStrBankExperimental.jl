```
RequestOptions(; kwargs...)
```

The options used to connect to an FTP server.

# Keywords

  * `hostname::AbstractString="localhost"`: the hostname or address of the FTP server.
  * `username::AbstractString=""`: the username used to access the FTP server.
  * `password::AbstractString=""`: the password used to access the FTP server.
  * `implicit::Bool=false`: use an implicit FTPS configuration.
  * `ssl::Bool=false`: use a secure connection. Typically specified for explicit FTPS.
  * `verify_peer::Bool=true`: verify authenticity of peer's certificate.
  * `active_mode::Bool=false`: use active mode to establish data connection.
