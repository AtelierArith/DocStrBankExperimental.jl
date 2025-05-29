```
ftp_command(
    options::RequestOptions,
    cmd::AbstractString;
    verbose::Union{Bool,IOStream}=false,
)
```

Pass FTP command with non-persistent connection. Returns a `Response`.
