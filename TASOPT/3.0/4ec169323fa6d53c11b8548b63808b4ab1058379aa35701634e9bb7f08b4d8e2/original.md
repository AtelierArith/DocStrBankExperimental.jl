```
quicksave_aircraft(ac::TASOPT.aircraft=TASOPT.read_aircraft_model(),
    filepath=joinpath(TASOPT.__TASOPTroot__, "IO/default_quicksave_aircraft.jld2"))
```

Serializes and saves aircraft `struct` to a .jld2 using JLD2 (not human-readable). Intended to store aircraft models with ALL fields (since not everything is stored by save*aircraft*model).

!!! details "🔃 Inputs and Outputs"
    **Inputs:**

      * `ac::TASOPT.aircraft`: TASOPT aircraft `struct` containing model in any state.
      * `filepath::String`: path and name of .jld2 file to be written.

    **Outputs:**

      * None.

