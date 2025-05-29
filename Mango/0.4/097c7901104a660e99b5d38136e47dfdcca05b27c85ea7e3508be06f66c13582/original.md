```
create_mqtt_container(host, port, client_id; codec=nothing)
```

Create a container using an MQTT protocol. 

The `host` is expected to be the IP-adress of the broker, `port` is the port of the broker,  the `client_id` is the id of the client which will be created and connected to the broker.  Optionally you can also provide a codec as tuple of functions (first encode, second decode, see  [`encode`](@ref) and [`decode`](@ref)).

# Examples

```julia
agent = create_mqtt_container("127.0.0.1", 5555, "MyClient")
```
