```
struct Network
    name::Symbol
    nodes::DataStructures.OrderedDict{Symbol,Node}
    migration::DataStructures.OrderedDict{DataType},Array{Matrix{Float64},2}}
    locations_key_map
end
```

Data for multiple interconnected spatial nodes.

# Arguments

  * `name::Symbol`: Name of network, usually location-relevant.
  * `nodes::DataStructures.OrderedDict{Symbol,Node}`: Dictionary of data for nodes included in network (metapopulation).
  * `migration::DataStructures.OrderedDict{DataType}, Array{Matrix{Float64},2}}`: Data defining species, genotype, and stage-specific transition rates. Entries default to zero.
  * `locations_key_map`: Mapping of node location information. Used to assign transition rates.
