```
findall_nan_chunks(x)
```

Finds the `(start, stop)` indices of each `NaN` chunk in `x` and returns a vector  of index tuples for the `NaN` ranges.

See also: [`findall_nan_chunks!`](@ref)

## Examples

```julia
x = [NaN, NaN, 2.3, NaN, 5.6, NaN, NaN, NaN]
findall_nan_chunks(x)
```
