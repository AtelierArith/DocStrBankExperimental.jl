```
constraint_tank_volume(
    wm::AbstractWaterModel,
    n_1::Int,
    n_2::Int,
    i::Int,
    time_step::Float64
)
```

Adds a constraint that integrates the volume of a tank forward in time. Here, `wm` is the WaterModels object, `n_1` is the index of a subnetwork within a multinetwork, `n_2` is the index of another subnetwork forward in time, relative to `n_1`, i is the index of the tank, and `time_step` is the time step of the interval from network `n_1` to `n_2`.
