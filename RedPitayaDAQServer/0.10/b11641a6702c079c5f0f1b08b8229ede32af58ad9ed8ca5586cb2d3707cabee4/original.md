```
RedPitayaCluster(hosts::Vector{String} [, port = 5025])
```

Construct a `RedPitayaCluster`.

During the construction the first host is labelled the master RedPitaya of a cluster and all RedPitayas are set to using the `EXTERNAL` trigger mode.

See also [`RedPitaya`](@ref), [`master`](@ref).

# Examples

```julia
julia> rpc = RedPitayaCluster(["192.168.1.100", "192.168.1.101"]);

julia> rp = master(rpc)

julia> rp == rpc[1]
true
```
