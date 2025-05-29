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
    The url from which the server is reachable, used to declare resources in Bonitos HTML and to establish a websocket connection.
    Setting it to `""` or `nothing` will use the url the server listens to.
    So, if `listen_url="127.0.0.1"`, this will default to http://localhost:forwarded_port (same as `local_url(server, "")`).
    You can also set this to `"."` to use relative urls, e.g. for accessing the webpage on a local network, or when serving it online with your own server.
    This is the preferred option for serving a whole website via Bonito, where you dont know in advanced where the page will be served.
    If it's more complicated, e.g. when the HTML is served on a different url from the url to proxy through to the Bonito server,
     a full URL needs to set, e.g. `proxy_url=https://bonito.makie.org`.
```
