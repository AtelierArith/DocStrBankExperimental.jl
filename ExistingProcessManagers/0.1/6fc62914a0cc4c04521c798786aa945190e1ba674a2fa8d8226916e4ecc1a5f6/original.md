```
parse_julia_worker_output_to_hosts_and_ports(; regex = julia_worker_regex)
```

Parse the output printed by Julia workers and return a list of hosts and ports.

## Example

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> worker_output = """
       julia_worker:9960#192.168.1.151
       julia_worker:9962#192.168.1.153
       julia_worker:9964#192.168.1.155
       julia_worker:9966#192.168.1.157
       julia_worker:9968#192.168.1.159
       """;

julia> hosts_and_ports = parse_julia_worker_output_to_hosts_and_ports(worker_output);
```

Now you can do either of the following two options, which are equivalent:

Option 1:

```julia
julia> addprocs(ExistingProcessManager(hosts_and_ports))
```

Option 2:

```julia
julia> addprocs_existing(hosts_and_ports)
```
