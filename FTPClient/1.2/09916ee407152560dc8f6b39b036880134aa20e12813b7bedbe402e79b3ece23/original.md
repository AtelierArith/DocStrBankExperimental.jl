```
Response
```

The response returned from a connection to an FTP server.

# Parameters

  * `body::IO`: contains the result of a command from ftp*command.   or the content of a downloaded file from ftp*get (if no destination file was defined).
  * `headers::Array{AbstractString}`: the header responses from the server.
  * `code::UInt`: the last header response code from the server.
  * `total_time::Float64`: the time the connection took.
  * `bytes_recd::Int`: the amount of bytes transmitted from the server (the file size in the   case of ftp_get).
