```
hosts_and_ports_to_workerconfigs(hosts_and_ports::Vector{Tuple{String, Int}})
```

Convert a list of hosts and port numbers to a list of `WorkerConfig`s.

## Example

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> hosts_and_ports = [
       ("127.0.0.1", 9601), # the host is "127.0.0.1", and the port number is 9601
       ("127.0.0.1", 9602), # the host is "127.0.0.1", and the port number is 9602
       ];

julia> wconfigs = hosts_and_ports_to_workerconfigs(hosts_and_ports);
```

Now you can do either of the following two options, which are equivalent:

Option 1:

```julia
julia> addprocs(ExistingProcessManager(wconfigs))
```

Option 2:

```julia
julia> addprocs_existing(wconfigs)
```
