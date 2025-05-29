```
prognostic_vars(canopy::CanopyModel)
```

Returns the prognostic variables for the canopy model by looping over each sub-component name in `canopy_components`.

This relies on the propertynames of `CanopyModel` being the same as those returned by `canopy_components`.
