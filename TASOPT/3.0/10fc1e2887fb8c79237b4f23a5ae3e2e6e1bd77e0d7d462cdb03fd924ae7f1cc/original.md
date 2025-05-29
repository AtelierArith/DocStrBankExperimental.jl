```
read_aircraft_model(datafile; 
defaultfile = joinpath(TASOPT.__TASOPTroot__, "../example/defaults/default_input.toml"))
```

Reads a specified TOML file that describes a TASOPT `aircraft` model  with a fall back to the default `aircraft` definition  provided in "/example/defaults/default_input.toml""

!!! note "Deviating from default"
    Extending `read_input.jl` and `save_model.jl` is recommended for models deviating appreciably  from the default functionality. Thorough knowledge of the model is required.


# Examples

```julia-repl
julia> read_aircraft_model("examples/defaults/default_input.toml")


┌ Info: engine_location not found in user specified input file. 
│ Reading engine_location from default TASOPT input:
│ 
│ engine_location = wing
└ 

┌ Info: pylon_weight_fraction not found in user specified input file. 
│ Reading pylon_weight_fraction from default TASOPT input:
│ 
│ pylon_weight_fraction = 0.1
└ 
Name: Example TASOPT Model;
Wpay = 210.0 kN
Des. Range  = 5.56e6 km
Cruise Mach = 0.8

```
