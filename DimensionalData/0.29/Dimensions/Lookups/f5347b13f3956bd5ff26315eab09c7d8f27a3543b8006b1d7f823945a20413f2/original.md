```
Contains <: IntSelector

Contains(x)
Contains(a, b)
```

Selector that selects the interval the value is contained by. If the interval is not present in the lookup, an error will be thrown.

Can only be used for [`Intervals`](@ref) or [`Categorical`](@ref). For [`Categorical`](@ref) it falls back to using [`At`](@ref). `Contains` should not be confused with `Base.contains` - use `Where(contains(x))`  to check for if values are contain in categorical values like strings.

`x` can be any value to select a single index, or a `Vector` of values to select vector of indices. If two values `a` and `b`  are used, the range between them will be selected.

## Example

```jldoctest
using DimensionalData; const DD = DimensionalData
dims_ = X(10:10:20; sampling=DD.Intervals(DD.Center())),
        Y(5:7; sampling=DD.Intervals(DD.Center()))
A = DimArray([1 2 3; 4 5 6], dims_)
A[X(Contains(8)), Y(Contains(6.8))]

# output
3
```
