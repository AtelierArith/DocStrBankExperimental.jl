```
constraint_on_off_regulator_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
    head_setting::Float64
)
```

Adds constraints that model the effects of a pressure-reducing valve (i.e., a regulator). When the regulator is operational (active), the regulator will ensure head at the node indexed by `node_to` will be equal to `head_setting`. When the regulator is inactive, heads at connecting nodes are decoupled. Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the regulator, `node_fr` is the index of the tail node of the regulator, `node_to` is the index of the head node of the regulator, and `head_setting` is the value of head to be set (if the regulator is active) at the (thus downstream) node indexed by `node_to`.
