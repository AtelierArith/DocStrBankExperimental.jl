```
configure_server!(;
        listen_url::String=SERVER_CONFIGURATION.listen_url[],
        listen_port::Integer=SERVER_CONFIGURATION.listen_port[],
        forwarded_port::Integer=listen_port,
        proxy_url=nothing,
        content_delivery_url=nothing
    )
```

Configures the parameters for the automatically started server.

```
Parameters:

* listen_url=SERVER_CONFIGURATION.listen_url[]
    The address the server listens to.
    must be 0.0.0.0, 127.0.0.1, ::, ::1, or localhost.
    If not set differently by an ENV variable, will default to 127.0.0.1

* listen_port::Integer=SERVER_CONFIGURATION.listen_port[],
    The Port to which the default server listens to
    If not set differently by an ENV variable, will default to 9384

* forwarded_port::Integer=listen_port,
    if port gets forwarded to some other port, set it here!

* proxy_url=nothing
    The url from which the server is reachable.
    If served on "127.0.0.1", this will default to http://localhost:forwarded_port
    if listen_url is "0.0.0.0", this will default to http://$(Sockets.getipaddr()):forwarded_port
    so that the server is reachable inside the local network.
    If the server should be reachable from some external dns server,
    this needs to be set here.
```
