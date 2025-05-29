```
bitonic_merge(input_a::Vec{N,T}, input_b::Vec{N,T}) where {N,T}
```

Merges two `SIMD.Vec` objects of the same type and size using a bitonic sort network. The inputs are assumed to be sorted. Returns a pair of vectors with the first and second halves of the merged sequence.
