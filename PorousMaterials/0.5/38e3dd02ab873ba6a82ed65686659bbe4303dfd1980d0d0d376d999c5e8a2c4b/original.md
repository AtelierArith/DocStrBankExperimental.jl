```
fluid = PengRobinsonFluid(fluid)
```

Reads in critical temperature, critical pressure, and acentric factor of the `fluid::Symbol` from the properties .csv file `joinpath(PorousMaterials.rc[:paths][:data], "PengRobinson_fluid_props.csv")` and returns a complete `PengRobinsonFluid` data structure. **NOTE: Do not delete the last three comment lines in PengRobinson*fluid*props.csv

# Arguments

  * `fluid::Symbol`: The fluid molecule you wish to construct a PengRobinsonFluid struct for

# Returns

  * `PengRobinsonFluid::struct`: Data structure containing Peng-Robinson fluid parameters.
