```
ftp(
    code::Function;
    hostname::AbstractString="", implicit::Bool=false, ssl::Bool=false,
    verify_peer::Bool=true, active_mode::Bool=false, username::AbstractString="",
    password::AbstractString="", verbose::Union{Bool,IOStream}=false,
)
```

Execute Function "code" on FTP server.
