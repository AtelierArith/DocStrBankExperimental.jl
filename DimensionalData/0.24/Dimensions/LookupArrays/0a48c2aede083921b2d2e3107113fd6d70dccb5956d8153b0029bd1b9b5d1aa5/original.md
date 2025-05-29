```
Between <: ArraySelector

Between(a, b)
```

Depreciated: use `a..b` instead of `Between(a, b)`. Other `Interval` objects from IntervalSets.jl, like `OpenInterval(a, b) will also work, giving the correct open/closed boundaries.

`Between` will e removed in furture to avoid clashes with `DataFrames.Between`.

Selector that retreive all indices located between 2 values, evaluated with `>=` for the lower value, and `<` for the upper value. This means the same value will not be counted twice in 2 adjacent `Between` selections.

For [`Intervals`](@ref) the whole interval must be lie between the values. For [`Points`](@ref) the points must fall between the values. Different [`Sampling`](@ref) types may give different results with the same input - this is the intended behaviour.

`Between` for [`Irregular`](@ref) intervals is a little complicated. The interval is the distance between a value and the next (for `Start` locus) or previous (for [`End`](@ref) locus) value.

For [`Center`](@ref), we take the mid point between two index values as the start and end of each interval. This may or may not make sense for the values in your indes, so use `Between` with `Irregular` `Intervals(Center())` with caution.

## Example

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(Between(15, 25)), Y(Between(4, 6.5))]

# output

1×2 DimArray{Int64,2} with dimensions:
  X Sampled{Int64} 20:10:20 ForwardOrdered Regular Points,
  Y Sampled{Int64} 5:6 ForwardOrdered Regular Points
     5  6
 20  4  5
```
