```
findall_nan_chunks!(v, x)
```

Finds the (start,a stop) indices of each `NaN` chunk in `x` and returns a vector  of those index tuples, using a preallocated boolean vector `v`, where  `length(x) == length(v)`, to keep track of `NaN` positions.

See also: [`findall_nan_chunks`](@ref)

## Example

```julia
x = [NaN, NaN, 2.3, NaN, 5.6, NaN, NaN, NaN]
v = zeros(Bool, length(x))
findall_nan_chunks!(v, x)
```
