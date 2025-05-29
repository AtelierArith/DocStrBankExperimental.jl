```julia
randPermutation(n; fix) 
```

  * `n` : dimension
  * `fix` : a keyword argument, default is set to `fix = 0`. If `fix = x`, `randPermutation(n,x)` will have atleast `x` fixed points

# Examples

Generates a random 5 by 5 permutation matrix

```julia
randPermutation(5)

5×5 SparseArrays.SparseMatrixCSC{Int8, Int64} with 5 stored entries:
 ⋅  ⋅  ⋅  ⋅  1
 ⋅  1  ⋅  ⋅  ⋅
 1  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  1  ⋅
```

Generates  Generates a random 10 by 10 permutation matrix with atleast 7 fix points

```julia
randPermutation(10, fix = 7)

10×10 SparseArrays.SparseMatrixCSC{Int8, Int64} with 10 stored entries: 
 1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋮              ⋮
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1

```
