```
addprocs_existing(x; kwargs...)
```

Equivalent to `addprocs(ExistingProcessManager(x); kwargs...)`.

## Examples

### Example 1

```julia
julia> hosts_and_ports = [
       ("127.0.0.1", 9601), # the host is "127.0.0.1", and the port number is 9601
       ("127.0.0.1", 9602), # the host is "127.0.0.1", and the port number is 9602
       ]
2-element Vector{Tuple{String, Int64}}:
 ("127.0.0.1", 9601)
 ("127.0.0.1", 9602)

julia> addprocs_existing(hosts_and_ports; kwargs...)
```

### Example 2

```julia
julia> w1 = WorkerConfig();

julia> w1.host = "127.0.0.1";

julia> w1.port = 9601;

julia> w2 = WorkerConfig();

julia> w2.host = "127.0.0.1";

julia> w2.port = 9602;

julia> wconfigs = WorkerConfig[w1, w2];

julia> addprocs_existing(wconfigs; kwargs...)
```

### Example 3

```julia
julia> worker_output = """
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9966#192.168.1.157
       julia_worker:9968#192.168.1.159
       """;

julia> addprocs_existing(worker_output; kwargs...)
```
