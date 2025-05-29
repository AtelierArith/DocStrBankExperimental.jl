```
nblocks(A[, i])
```

Return the number of blocks in the range and domain of the `Jets` block operator `A::Union{Jet, Jop}`. With `i` specified, return `nblocks(range(jet))` for `i = 1` and return `nblocks(domain(jet))` otherwise.
