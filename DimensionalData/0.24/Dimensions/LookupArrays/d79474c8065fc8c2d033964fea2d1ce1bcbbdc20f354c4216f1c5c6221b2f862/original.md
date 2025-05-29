```
At <: IntSelector

At(x, atol, rtol)
At(x; atol=nothing, rtol=nothing)
```

Selector that exactly matches the value on the passed-in dimensions, or throws an error. For ranges and arrays, every intermediate value must match an existing value - not just the end points.

`x` can be any value or `Vector` of values.

`atol` and `rtol` are passed to `isapprox`. For `Number` `rtol` will be set to `Base.rtoldefault`, otherwise `nothing`, and wont be used.

## Example

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(At(20)), Y(At(6))]

# output

5
```
