```
rand(::Type{SymmetricTensor{T, N}}, n::Int, b::Int = 2)
```

Return an $N$-dimmensional random `SymmetricTensor` with elements of type `T` drawn from a uniform distribution on $[0, 1)$, where `n` denotes the data size and `b` denotes the block size.
