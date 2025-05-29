```
ffindnz(arr)
```

Return the nonzero elements of `arr`, as Finch understands `arr`. Returns `(I..., V)`, where `I` are the coordinate vectors, one for each mode of `arr`, and `V` is a vector of corresponding nonzero values, which can be passed to [`fsparse`](@ref).

See also: (`findnz`)(https://docs.julialang.org/en/v1/stdlib/SparseArrays/#SparseArrays.findnz)
