```
constraint_tank_volume_recovery(
    wm::AbstractWaterModel,
    i::Int,
    n_1::Int,
    n_f::Int
)
```

Adds a constraint that ensures the volume of a tank at the end of the time horizon is greater than or equal to the volume of the tank at the beginning of the time horizon. Here, `wm` is the WaterModels object, `i` is the index of the tank, `n_1` is the index of the first subnetwork within a multinetwork, and `n_f` is the index of the final subnetwork. Also updates the minimum head in the `ref` dictionary for node `i` at the final subnetwork index `n_f` to take the minimum head value at `n_1` if it is larger, as implied by this constraint.
