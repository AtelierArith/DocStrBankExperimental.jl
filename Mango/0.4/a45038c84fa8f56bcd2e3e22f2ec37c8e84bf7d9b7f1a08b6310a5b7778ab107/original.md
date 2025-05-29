```
create_tcp_container(host, port; codec=nothing)
```

Create a container using an TCP protocol. 

The `host` is expected to be the IP-adress to bind on, `port` is the port to bind on. Optionally you  can also provide a codec as tuple of functions (first encode, second decode, see  [`encode`](@ref) and [`decode`](@ref)).

# Examples

```julia
agent = create_mqtt_container("127.0.0.1", 5555, "MyClient")
```
