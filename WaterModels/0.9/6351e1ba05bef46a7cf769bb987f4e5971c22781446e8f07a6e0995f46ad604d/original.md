```
constraint_on_off_valve_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int
)
```

Adds constraints that model head difference between the nodes connected by a valve based on the operating status of the valve (i.e., heads at connecting nodes are decoupled if the valve is inactive, but if the valve is active, the heads at connecting nodes are equal). Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the valve, `node_fr` is the index of the tail node of the valve, and `node_to` is the index of the head node of the valve.
