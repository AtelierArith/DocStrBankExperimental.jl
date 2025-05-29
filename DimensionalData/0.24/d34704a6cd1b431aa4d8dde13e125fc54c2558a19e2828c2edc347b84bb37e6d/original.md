```
reorder(A::AbstractDimArray, order::Pair) => AbstractDimArray
reorder(A::Dimension, order::Order) => AbstractDimArray
```

Reorder every dims index/array to `order`, or reorder index for the the given dimension(s) to the `Order` they wrap.

`order` can be an [`Order`](@ref), or `Dimeension => Order` pairs.

If no axis reversal is required the same objects will be returned, without allocation.
