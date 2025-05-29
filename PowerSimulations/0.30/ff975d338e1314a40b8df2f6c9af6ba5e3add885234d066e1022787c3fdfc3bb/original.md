```julia
set_system!(
    results::PowerSimulations.SimulationProblemResults,
    system::AbstractString
)

```

Set the system in the results instance.

Throws InvalidValue if the system UUID is incorrect.

# Arguments

  * `results::SimulationProblemResults`: Results object
  * `system::AbstractString`: Path to the system json file

# Examples

```julia
julia > set_system!(res, "my_path/system_data.json")
```
