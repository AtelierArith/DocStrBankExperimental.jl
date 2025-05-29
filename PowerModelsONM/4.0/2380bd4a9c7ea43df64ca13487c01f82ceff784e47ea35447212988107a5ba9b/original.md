```
parse_network!(args::Dict{String,<:Any})::Dict{String,Any}
```

In-place version of [`parse_network`](@ref parse_network), returns the ENGINEERING multinetwork data structure, which is available in `args` under `args["network"]`, and adds the non-expanded ENGINEERING data structure under `args["base_network"]`
