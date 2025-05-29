```
pointwise_cross!(C::VectorData,A::ScalarData/VectorData,B::VectorData/ScalarData) -> VectorData
```

Compute the cross product between the point data `A` and `B`, one of which is scalar data and treated as an out-of-plane component of a vector, while the other is in-plane vector data, and return the result as vector data `C`.
