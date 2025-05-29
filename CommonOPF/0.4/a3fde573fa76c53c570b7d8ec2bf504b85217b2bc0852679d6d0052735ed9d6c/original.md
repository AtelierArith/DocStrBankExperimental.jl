```
init_split_networks!(mg::MetaGraphsNext.MetaGraph; init_vs::Dict = Dict())
```

Use the `:load_sum_order` in `mg` to `init_split_networks!` in the correct order, i.e. set the loads at the leaf - substation connections as sums of all the loads (and the voltages at substations)
