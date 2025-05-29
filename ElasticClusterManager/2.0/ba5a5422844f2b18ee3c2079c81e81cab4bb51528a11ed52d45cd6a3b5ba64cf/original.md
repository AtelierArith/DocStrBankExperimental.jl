```
ElasticClusterManager.elastic_worker(
    cookie::AbstractString, addr::AbstractString="127.0.0.1", port::Integer = 9009;
    forward_stdout::Bool = true,
    Base.@nospecialize(env::AbstractVector = [],)
)
```

Start an elastic worker process that connects to the main Julia process at IP-address `addr` and port `port`.

Does not return.
