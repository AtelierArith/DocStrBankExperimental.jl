```
ExistingProcessManager(hosts_and_ports::Vector{Tuple{String, Int}})
```

Construct an `ExistingProcessManager` from a list of hosts and port numbers.

## Example

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> hosts_and_ports = [
       ("127.0.0.1", 9601), # the host is "127.0.0.1", and the port number is 9601
       ("127.0.0.1", 9602), # the host is "127.0.0.1", and the port number is 9602
       ];

julia> manager = ExistingProcessManager(hosts_and_ports);
```

Now you can do:

```julia
julia> addprocs(manager)
```
