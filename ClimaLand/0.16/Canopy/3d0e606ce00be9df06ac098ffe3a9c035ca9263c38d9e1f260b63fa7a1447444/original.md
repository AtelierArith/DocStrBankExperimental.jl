```
prognostic_types(canopy::CanopyModel)
```

Returns the prognostic types for the canopy model by looping over each sub-component name in `canopy_components`.

This relies on the propertynames of `CanopyModel` being the same as those returned by `canopy_components`.
