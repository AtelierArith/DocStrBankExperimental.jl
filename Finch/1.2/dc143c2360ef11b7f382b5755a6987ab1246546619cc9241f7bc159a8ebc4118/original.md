```
fsparse(I::Tuple, V,[ M::Tuple, combine]; fill_value=zero(eltype(V)))
```

Create a sparse COO tensor `S` such that `size(S) == M` and `S[(i[q] for i = I)...] = V[q]`. The combine function is used to combine duplicates. If `M` is not specified, it is set to `map(maximum, I)`. If the combine function is not supplied, combine defaults to `+` unless the elements of V are Booleans in which case combine defaults to `|`. All elements of I must satisfy 1 <= I[n][q] <= M[n].  Numerical zeros are retained as structural nonzeros; to drop numerical zeros, use dropzeros!.

See also: [`sparse`](https://docs.julialang.org/en/v1/stdlib/SparseArrays/#SparseArrays.sparse)

# Examples

julia> I = (     [1, 2, 3],     [1, 2, 3],     [1, 2, 3]);

julia> V = [1.0; 2.0; 3.0];

julia> fsparse(I, V) SparseCOO (0.0) [1:3×1:3×1:3] │ │ │ └─└─└─[1, 1, 1] [2, 2, 2] [3, 3, 3]       1.0       2.0       3.0
