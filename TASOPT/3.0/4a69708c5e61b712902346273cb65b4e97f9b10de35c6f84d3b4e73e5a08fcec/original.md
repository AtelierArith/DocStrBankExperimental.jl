```
save_aircraft_model(ac::TASOPT.aircraft=TASOPT.read_aircraft_model(), 
datafile=joinpath(TASOPT.__TASOPTroot__, "IO/default_output.toml"),
save_output::Bool=false)
```

Converts an aircraft model into a dictionary and writes  it to a TOML file. Values to be written are explicitly set following the default_input.toml. All values are written in SI units.

This save operation makes add'l* assumptions about parameter repetition. Namely: The same value is applied for all flight segments/points for:     - parm[] parameters     - excrescence*drag*factors, wing overspeeds, wing/stabilizer Re_refs The same value is applied for all missions and flight segments for:     - parg[] and pare[] parameters     - fuel temperature

Said value is the first entry in the corresponding array axis,  except for some aero parameters where other points are more relevant (e.g., "Cruise" "Takeoff").

*and modifiable

!!! note "Deviating from default"
    Extending `read_input.jl` and `save_model.jl` is recommended for models deviating appreciably  from the default functionality. Thorough knowledge of the model is required.

