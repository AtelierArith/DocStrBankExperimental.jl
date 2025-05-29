```
Touches <: ArraySelector

Touches(a, b)
```

Selector that retrieves all indices touching the closed interval 2 values, for the maximum possible area that could interact with the supplied range.

This can be better than `..` when e.g. subsetting an area to rasterize, as you may wish to include pixels that just touch the area, rather than those that fall within it.

Touches is different to using closed intervals when the lookups also contain intervals - if any of the intervals touch, they are included. With `..` they are discarded unless the whole cell interval falls inside the selector interval.

## Example

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(5:7)))
A[X(Touches(15, 25)), Y(Touches(4, 6.5))]

# output
┌ 1×2 DimArray{Int64, 2} ┐
├────────────────────────┴───────────────────────────── dims ┐
  ↓ X Sampled{Int64} 20:10:20 ForwardOrdered Regular Points,
  → Y Sampled{Int64} 5:6 ForwardOrdered Regular Points
└────────────────────────────────────────────────────────────┘
  ↓ →  5  6
 20    4  5
```
