```
Where <: ArraySelector

Where(f::Function)
```

Selector that filters a dimension lookup by any function that accepts a single value and returns a `Bool`.

## Example

```jldoctest
using DimensionalData

A = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(19:21)))
A[X(Where(x -> x > 15)), Y(Where(x -> x in (19, 21)))]

# output

1×2 DimArray{Int64,2} with dimensions:
  X Sampled{Int64} Int64[20] ForwardOrdered Regular Points,
  Y Sampled{Int64} Int64[19, 21] ForwardOrdered Regular Points
     19  21
 20   4   6
```
