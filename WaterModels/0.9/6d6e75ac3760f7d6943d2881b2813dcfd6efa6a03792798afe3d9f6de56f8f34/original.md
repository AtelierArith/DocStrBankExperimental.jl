```
constraint_on_off_pump_switch(
    wm::AbstractWaterModel,
    a::Int,
    network_ids::Array{Int,1},
    max_switches::Int
)
```

Adds a constraint that limits the number of times a pump can be switched from off to on in a multiperiod pump scheduling problem. Here, `wm` is the WaterModels object, `a` is the index of the pump, `network_ids` are the network (time) indices used in the summation that limits the number of switches, and `max_switches` is the number of maximum switches permitted for the pump over the set of network indices.
