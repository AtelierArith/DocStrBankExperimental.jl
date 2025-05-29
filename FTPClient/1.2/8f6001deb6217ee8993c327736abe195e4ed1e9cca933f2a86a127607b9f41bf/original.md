```
ConnContext
```

Keeps track of a persistent FTP connection.

# Arguments

  * `url::AbstractString`: url of the FTP server.
  * `options::RequestOptions`: the options used for the connection.

# Keywords

  * `verbose::Union{IOStream,Bool}=false`: an `IOStream` to capture LibCURL's output or a `Bool`, if true output is written to STDERR.
