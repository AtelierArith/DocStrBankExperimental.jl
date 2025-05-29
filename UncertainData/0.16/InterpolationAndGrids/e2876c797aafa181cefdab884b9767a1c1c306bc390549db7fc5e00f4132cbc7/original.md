```
fill_nans!(x, intp::Linear)
```

Fill `NaN` values in `x` in-place using linear interpolation. `NaN`s at  the left or right edges of `x` are not interpolated, but left as they are. See also [`fill_nans`](@ref).

## Example

```julia
x = [NaN, 1.4, 5.6, NaN, 4.3, 3.1, NaN, NaN, 5.6, NaN]
fill_nans!(x, Linear())
```
