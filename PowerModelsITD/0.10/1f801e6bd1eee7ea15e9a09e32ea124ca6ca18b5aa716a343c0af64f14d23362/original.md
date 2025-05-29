```
function replicate(
    sn_data::Dict{String,<:Any},
    count::Int;
    global_keys::Set{String}=Set{String}()
)
```

Turns in given single network pmitd data in multinetwork data with a `count` replicate of the given network. Note that this function performs a deepcopy of the network data. Significant multinetwork space savings can often be achieved by building application specific methods of building multinetwork with minimal data replication. `sn_data` is the data to be replicated, `count` is the number of networks to be replicated.
