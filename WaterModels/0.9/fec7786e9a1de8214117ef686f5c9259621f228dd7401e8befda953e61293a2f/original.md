```
constraint_on_off_pump_head_gain(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
    q_min_forward::Float64
)
```

Adds constraints that model the pump's head gain, if operating, as a possibly nonlinear function of flow rate. If the pump is inactive, the head gain is restricted to a value of zero. Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the pump, `node_fr` is the index of the tail node of the pump, `node_to` is the index of the head node of the pump, and `q_min_forward` is the *minimum* (positive) amount of flow when the pump is active. Head gain is assumed to be a nonnegative quantity that is directed from `node_fr` to `node_to`.
