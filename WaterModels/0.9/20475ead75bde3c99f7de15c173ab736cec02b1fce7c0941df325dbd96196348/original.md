```
constraint_on_off_pump_switch(
    wm::AbstractWaterModel,
    a::Int;
    network_ids::Array{Int,1};
    kwargs...
)
```

Constraint template to add [`constraint_on_off_pump_switch`](@ref) constraint, which limits the number of times a pump can be switched from off to on in a multiperiod pump scheduling problem. Here, `wm` is the WaterModels object, `a` is the index of the pump, and `network_ids` are the network (time) indices used in the summation that limits the number of switches.
