```
function constraint_transmission_power_balance_boundary(
    pmitd::AbstractPowerModelITD,
    i::Int;
    nw_pmitd::Int=nw_id_default
)
```

General power balance contraints for boundary buses in the transmission system-side.
