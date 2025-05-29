```
function constraint_boundary_current(
    pmitd::AbstractIVRPowerModelITD,
    i::Int;
    nw::Int=nw_id_default
)
```

AbstractIVRPowerModelITDの矩形電流（I）に基づく境界電力制約。
