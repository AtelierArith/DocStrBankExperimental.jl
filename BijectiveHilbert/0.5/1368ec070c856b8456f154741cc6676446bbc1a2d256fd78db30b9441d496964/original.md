```
encode_hilbert_zero(ha::HilbertAlgorithm{T}, X::Vector{A})
```

Takes an n-dimensional vector `X` and returns a single integer of type `T` which orders `X` to improve spatial locality. The input `X` has multiple axes and the output is called a Hilbert index. This version is zero-based, so each axis counts from 0, and the smallest Hilbert index is 0.
