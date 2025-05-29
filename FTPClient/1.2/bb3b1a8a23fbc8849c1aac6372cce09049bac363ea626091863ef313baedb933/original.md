```
FTP(url; kwargs...)
```

Connect to an FTP server using the information specified in the URI.

# Keywords

  * `verify_peer::Bool=true`: verify the authenticity of the peer's certificate.
  * `active_mode::Bool=false`: use active mode to establish data connection.

# Example

```julia
julia> FTP("ftp://user:password@ftp.example.com");  # FTP connection with no security

julia> FTP("ftpes://user:password@ftp.example.com");  # Explicit security (FTPES)

julia> FTP("ftps://user:password@ftp.example.com");  # Implicit security (FTPS)
```
