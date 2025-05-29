```
constraint_flow_conservation(
    wm::AbstractWaterModel,
    i::Int;
    nw::Int=nw_id_default
)
```

Constraint template to add constraints that ensure volumetric flow rate (and thus mass) is conserved at node `i` and subnetwork (or time) index `nw` in the network. Here, `wm` is the WaterModels object.
