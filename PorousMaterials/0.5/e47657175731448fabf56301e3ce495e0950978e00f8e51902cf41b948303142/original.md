```
fluid = VdWFluid(fluid)
```

Reads in van der Waals constants of the `fluid::Symbol` from the properties .csv file `joinpath(PorousMaterials.rc[:paths][:data], "VdW_fluid_props.csv")` and returns a complete `VdWFluid` data structure. ***NOTE: Do not delete the last three comment lines in VdW*fluid*props.csv

# Arguments

  * `fluid::Symbol`: The fluid you wish to construct a VdWFluid struct for

# Returns

  * `VdWFluid::struct`: Data structure containing van der Waals constants
