```
Syslog <: IO
```

`Syslog` handles writing logs to local (libc inteface) and remote (UDP / TCP sockets) syslog servers.

# Fields

  * `address::Union{Tuple{IPAddr, Int}, Nothing}`: The host and ip for the remote servers. Logs locally if `nothing`.
  * `facility::Symbol`: The syslog facility to write to (e.g., :local0, :ft, :daemon, etc) (defaults to :user)
  * `socket::Union{Base.LibuvStream, Nothing}`: A UDP or TCP socket for logging messages. Logs locally if `nothing`.
