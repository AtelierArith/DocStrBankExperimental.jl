```
Near <: IntSelector

Near(x)
Near(a, b)
```

Selector that selects the nearest index to `x`.

With [`Points`](@ref) this is simply the lookup values nearest to the `x`, however with [`Intervals`](@ref) it is the interval *center* nearest to `x`. This will be offset from the index value for `Start` and [`End`](@ref) locus.

`x` can be any value to select a single index, or a `Vector` of values to select vector of indices. If two values `a` and `b`  are used, the range between the nearsest value to each of them will be selected.

## Example

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(Near(23)), Y(Near(5.1))]

# output
4
```
