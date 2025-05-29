```
create_network(name::String, network::AbstractDict)::StreamfallNetwork
```

Create a StreamNetwork from a YAML-derived specification.

# Example

```julia-repl
julia> using OrderedCollections
julia> network_spec = YAML.load_file("example_network.yml"; dicttype=OrderedDict{Any,Any})
julia> sn = create_network("Example Network", network_spec)
```
