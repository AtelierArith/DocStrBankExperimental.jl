```
DICE2023_NREG(n;kwargs...)
```

Build parameters for a DICE2023 world partitioned in n equal regions (unless parameters are overrided)

Create a parameters struct where the world is partitioned in n regions, and where each region is equal, with the same coefficients but with 1/n of initial emissions, capital, production, population, ...

Data is from DICE2013, so the output of `DICE2023_NREG(1)` is the same as `DICE2023()`.

Using the keyword arguments one can specify individual parameters that differ from DICE2023, with eventually a regional specification.

See [`DICEParameters`](@ref) for a complete list of available parameters and [`run_dice`](@ref) to run the optimization with the parameter struct created with this function.

# Example

```julia
four_regions_parameters = DICE2023_NREG(4) 
alt_dam_parameters      = DICE2023_NREG(2, a2base = [0.01, 0.02]) # two regions differing only for the a2base parameter
results = run_dice(four_regions_parameters)
```
