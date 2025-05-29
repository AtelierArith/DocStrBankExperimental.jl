```
reorder(A::Union{AbstractDimArray,AbstractDimStack}, order::Pair...)
reorder(A::Union{AbstractDimArray,AbstractDimStack}, order)
reorder(A::Dimension, order::Order)
```

Reorder every dims index/array to `order`, or reorder index for the given dimension(s) in `order`.

`order` can be an [`Order`](@ref), `Dimension => Order` pairs. A Tuple of Dimensions or any object that defines `dims` can be used in which case the dimensions of this object are used for reordering.

If no axis reversal is required the same objects will be returned, without allocation.

## Example

```jldoctest
using DimensionalData

# Create a DimArray
da = DimArray([1 2 3; 4 5 6], (X(10:10:20), Y(300:-100:100)))

# Reverse it
rev = reverse(da, dims=Y)

# using `da` in reorder will return it to the original order
reorder(rev, da) == da

# output
true
```
