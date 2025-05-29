```
constraint_on_off_pump_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int
)
```

Adds constraints that model head differences at the nodes connected by a pump based on the operating status of the pump (i.e., heads at connecting nodes are decoupled if the pump is inactive, but if the pump is active, the head difference is computed from the pump's head gain, which is a function of flow). Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the pump, `node_fr` is the index of the tail node of the pump, and `node_to` is the index of the head node of the pump.
