```
tensor_to_povm(A::Array{T,4}, o::Vector{Int})
```

Converts a set of measurements in the common tensor format into a matrix of (hermitian) matrices. By default, the second argument is fixed by the size of `A`. It can also contain custom number of outcomes if there are measurements with less outcomes.
