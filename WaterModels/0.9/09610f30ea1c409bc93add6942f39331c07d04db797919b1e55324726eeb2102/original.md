```
constraint_tank_volume_fixed(
    wm::AbstractWaterModel,
    n::Int,
    i::Int,
    V_0::Float64,
    time_step::Float64,
    min_vol::Float64,
    max_vol::Float64
)
```

Adds a constraint that ensures the volume of a tank at some time index is fixed. Here, `wm` is the WaterModels object, `n` is the index of a subnetwork within a multinetwork, `i` is the index of the tank, and `V_0` is the fixed volume of the tank that is desired. Also adds constraints that ensure, after integration of volume forward in time, the new volume will reside between predefined lower and upper bounds. To that end, `time_step` is the time step between the current time index and the next, `min_vol` is the minimum volume of water that must be present in the tank, and `max_vol` is the maximum volume of water in the tank.
