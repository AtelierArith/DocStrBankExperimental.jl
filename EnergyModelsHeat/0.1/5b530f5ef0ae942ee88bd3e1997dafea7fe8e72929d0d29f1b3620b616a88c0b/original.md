```
PinchData{T}
```

Data for fixed temperature intervals used to calculate available energy from surplus energy source operating at `T_SH_hot` and `T_SH_cold`, with `ΔT_min` between surplus source and the district heating network operating at `T_DH_hot` and `T_DH_cold`.

This struct is used internally, and it is calculated from the supply and return temperatures of the `ResourceHeat` going in and out of the `AbstractHeatExchanger`.
