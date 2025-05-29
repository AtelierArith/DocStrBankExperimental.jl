```
flatview(A::ArrayOfSimilarArrays{T,M,N,L,P})::P
```

Returns the array of dimensionality `L = M + N` wrapped by `A`. The shape of the result may be freely changed without breaking the inner consistency of `A`.
