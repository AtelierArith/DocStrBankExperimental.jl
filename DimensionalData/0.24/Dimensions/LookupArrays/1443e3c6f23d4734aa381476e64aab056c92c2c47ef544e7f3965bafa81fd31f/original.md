```
Near <: IntSelector

Near(x)
```

Selector that selects the nearest index to `x`.

With [`Points`](@ref) this is simply the index values nearest to the `x`, however with [`Intervals`](@ref) it is the interval *center* nearest to `x`. This will be offset from the index value for `Start` and [`End`](@ref) loci.

## Example

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(Near(23)), Y(Near(5.1))]

# output
4
```
