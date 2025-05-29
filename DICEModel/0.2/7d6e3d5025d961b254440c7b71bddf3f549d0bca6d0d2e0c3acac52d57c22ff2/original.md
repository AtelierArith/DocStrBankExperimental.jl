```
RICE2023(;kwargs...)
```

Build parameters calibrated to have the DICE2023 world totals and the 12-regions RICE2020 regional distribution.

Create a parameters struct where the world is partitioned in 12 regions, with coefficients of DICE2023 but a regional variance derived in most cases from RICE2020 (initial emissions, capital, production, population) or assumed (e.g. damages)

Note that the utility weights to provide to each region are exogenous (default to equal weights), they are NOT the Negishi weights. The `run_dice` function can eventually be used iteractively to look for these weights.

See [`DICEParameters`](@ref) for a complete list of available parameters and [`run_dice`](@ref) to run the optimization with the parameter struct created with this function.

# Example

```julia
w_rich  = [5,4,3,3,1,1,3,2,2,1,1.5,1] #
w_equal = fill(1,12)
res_cbopt_12r_poor = run_dice(RICE2023(;weights=w_poor))
res_cbopt_12r_rich = run_dice(RICE2023(;weights=w_rich)) 
```

# Notes

  * The default 12 regions are: ["USA", "EUS", "JPN", "OHI", "RUS", "EEC", "CHN", "IND", "MDE", "SSA", "LAA", "ROW"]
