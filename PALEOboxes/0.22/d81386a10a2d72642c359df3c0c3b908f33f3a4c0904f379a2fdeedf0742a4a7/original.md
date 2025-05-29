```
LinInterp(xvals, xperiod=0.0; require_sorted_input=true) -> LinInterp
```

Create a `LinInterp` struct for generic linear interpolation for (scalar) value `xval` into a set of records at `xvals`.

[`interp`](@ref) calculates weights and indices for the two records enclosing `xval`, hence allows use for arbitrary record types.

# Args:

```
- `xvals::Vector`: x values at which function is available.
- `xperiod=0.0`: Periodicity of x values (0.0 for not periodic)
- `require_sorted_input::Bool=true`: to check that input is sorted in ascending order, 
 `false` to allow arbitrary order (which will then be sorted for internal use).
```
