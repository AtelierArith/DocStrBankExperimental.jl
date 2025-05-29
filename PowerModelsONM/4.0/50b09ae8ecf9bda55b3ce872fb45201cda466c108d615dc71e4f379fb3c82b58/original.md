```
parse_network(
    network_file::String
)::Tuple{Dict{String,Any},Dict{String,Any}}
```

Parses network file given by runtime arguments into its base network, i.e., not expanded into a multinetwork, and multinetwork, which is the multinetwork `ENGINEERING` representation of the network.
