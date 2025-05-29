```
function infiltration_capacity(
    Y::ClimaCore.Fields.FieldVector,
    p::NamedTuple,
)
```

Function which computes the infiltration capacity of the soil based on soil characteristics, moisture levels, and pond height.

Defined such that positive means into soil.
