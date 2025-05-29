```
ExistingProcessManager(worker_output::AbstractString)
```

Construct an `ExistingProcessManager` from the output printed by Julia worker processes.

## Example

```jldoctest; setup = :(using ExistingProcessManagers; using Distributed)
julia> worker_output = """
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9960#192.168.1.151
       julia_worker:9966#192.168.1.157
       julia_worker:9968#192.168.1.159
       """;

julia> manager = ExistingProcessManager(worker_output);
```

Now you can do:

```julia
julia> addprocs(manager)
```
