```
init_split_networks!(nets::Vector{Network{SinglePhase}}; init_vs::Dict = Dict())
```

Set the loads on the upstream leaf nodes equal to the sum of all the loads in the downstream nodes. It is important that the order of `nets` is from leaf branches to trunk branches so that the sums of loads take into account all downstream sub-trees.

if `init_vs` is provided, the `net.v0` is set for the `Input` with its `net.substation_bus` equal      to the key in `init_vs`

```julia
init_vs = Dict(
    "sub_bus_1" => 0.98
)

for net in nets
    if net.substation_bus in keys(init_vs)
        net.v0 = init_vs[net.substation_bus]
    end
end
```
