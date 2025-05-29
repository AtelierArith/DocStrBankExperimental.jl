```
constraint_on_off_pump_group(
    wm::AbstractWaterModel,
    n::Int,
    k::Int,
    pump_indices::Set{Int}
)
```

Adds a constraint that imposes symmetry-breaking lexicographic sorting of pump activation statuses on groups of identical pumps operating in parallel along the same arc of the network. Reduces the combinatorial complexity of problems involving multiple pumps operating in parallel. Here, `wm` is the WaterModels object, `n` is the index of the subnetwork within a multinetwork, `k` is the index of the arc that includes the group of identical pumps, and `pump_indices` is the set of pump indices for pumps operating in parallel along arc `k`.
