```
parse_faults(
    faults_file::String;
    validate::Bool=true
)::Dict{String,Any}
```

Parses fault JSON input files which have the same structure as the outputs from `PowerModelsProtection.build_mc_fault_stuides`

## Expected JSON Structure

```json
{
    "bus_name": {
        "fault_type": {
            "fault_key": {
                "g": [ [200, -100, -100], [-100, 200, -100], [-100, -100, 200]],
                "b": [ [0, 0, 0], [0, 0, 0], [0, 0, 0]],
                "status": "ENABLED",
                "fault_type": "fault_type",
                "bus": "bus_name",
                "name": "fault_key",
                "connections": [1, 2, 3]
            }
        }
    }
}
```

where `"fault_type"` is one of:

  * `"3p"` : 3-phase
  * `"3pg"` : 3-phase-to-ground
  * `"ll"` : line-to-line
  * `"llg"` : line-to-line-to-ground
  * `"ll"` : line-to-line

"bus_name" is arbitrary, and just needs to match a bus's name in the network model.

`"status"` is a `PowerModelsDistribution.Status` Enum in `String` form, and must be either `"ENABLED"` or `"DISABLED"`.

`"g"` and `"b"` are matrices in SI units.

`"fault_type"` in the deepest level is merely metadata and should match the `"fault_type"` key above.

`"name"` should match the fault key and is required to be an `Integer`.

`"connections"` is a Vector of Integers indicating the phases that the fault applies to.

For more details see PowerModelsProtection's [documentation](https://github.io/lanl-ansi/PowerModelsProtection.jl)

## Validation

If `validate=true` (default), the parsed data structure will be validated against the latest [Faults Schema](@ref Faults-Schema).
