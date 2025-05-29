```
create_network(name::String, network::AbstractDict)::StreamfallNetwork
```

YAMLから派生した仕様からStreamNetworkを作成します。

# 例

```julia-repl
julia> using OrderedCollections
julia> network_spec = YAML.load_file("example_network.yml"; dicttype=OrderedDict{Any,Any})
julia> sn = create_network("Example Network", network_spec)
```
