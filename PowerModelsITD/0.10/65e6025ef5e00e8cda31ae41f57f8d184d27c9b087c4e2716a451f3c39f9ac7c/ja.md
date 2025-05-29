```
function constraint_boundary_power(
    pmitd::LPowerModelITD,
    i::Int;
    nw::Int=nw_id_default
)
```

LPowerModelITDの境界電力制約（線形バージョン - アクティブPのみ）。
