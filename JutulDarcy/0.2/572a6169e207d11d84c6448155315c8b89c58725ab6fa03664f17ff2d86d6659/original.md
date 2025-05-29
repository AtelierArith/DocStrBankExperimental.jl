```
SourceTerm(cell, value; fractional_flow = [1.0], type = MassSource)
```

Create source term in given `cell` with given total `value`.

The optional `fractional_flow` argument controls how this term is divided over components if used for inflow and should contain one entry per component in the system: (`number_of_components(system)`). `fractional_flow` should sum up to 1.0. The `type` argument should be an instance of the `FlowSourceType` enum, with interpretations as follows:

  * `MassSource`: Source is directly interpreted as component masses.
  * `StandardVolumeSource`: Source is volume at standard/surface conditions.  References densities are used to convert into mass sources.
  * `VolumeSource`: Source is volume at in-situ / reservoir conditions.
