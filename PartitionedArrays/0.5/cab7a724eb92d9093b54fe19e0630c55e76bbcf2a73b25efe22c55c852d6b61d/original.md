```
length_to_ptrs!(ptrs)
```

Compute the field `ptrs` of a [`JaggedArray`](@ref). `length(ptrs)` should be the number of sub-vectors in the jagged array plus one. At input, `ptrs[i+1]` is the length of the i-th sub-vector. At output, `ptrs[i]:(ptrs[i+1]-1)` contains the range where the i-th sub-vector is stored in the `data` field of the jagged array.
