```
call_count_nans_state(state, mask::ClimaCore.Fields.Field = nothing, verbose = false)
```

This calls the function which counts the number of NaNs in the state, e.g. the FieldVector given by `sol.u[end]` after calling `solve`. This function is useful for debugging simulations to determine quantitatively if a simulation is stable; this is only for use in non-column simulations.

If this function is called on a FieldVector, it will recursively call itself on each Field in the FieldVector. If it is called on a Field, it will count the number of NaNs in the Field and produce a warning if any are found; this behavior is different for 2d and 3d fields, which is why we dispatch on the `space`.

If a ClimaCore Field is provided as `mask`, the function will only count NaNs in the state variables where the mask is 1. This is intended to be used with the land/sea mask, to avoid counting NaNs over the ocean. Note this assumes the mask is 1 over land and 0 over ocean, and that the mask is a 2D field.

The `verbose` argument toggles whether the function produces output when no NaNs are found.
