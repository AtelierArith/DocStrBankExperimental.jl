```
At <: IntSelector

At(x; atol=nothing, rtol=nothing)
At(a, b; kw...)
```

Selector that exactly matches the value on the passed-in dimensions, or throws an error. For ranges and arrays, every intermediate value must match an existing value - not just the end points.

`x` can be any value to select a single index, or a `Vector` of values to select vector of indices. If two values `a` and `b` are used, the range between them will be selected.

Keyword `atol` is passed to `isapprox`.

## Example

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(At(20)), Y(At(6))]

# output

5
```
