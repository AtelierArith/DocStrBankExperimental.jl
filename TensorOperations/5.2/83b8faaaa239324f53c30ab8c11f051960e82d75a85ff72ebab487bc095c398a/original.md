```
tensorcopy!(C, A, pA::Index2Tuple, conjA=false, α=1, [backend, allocator])
```

Copy the contents of tensor `A` into `C`, where the dimensions `A` are permuted according to the permutation and repartition `pA`.

The result of this method is equivalent to `α * permutedims!(C, A, pA)`.

Optionally, the flag `conjA` can be used to specify whether the input tensor should be conjugated (`true`) or not (`false`). 

!!! warning
    The object `C` must not be aliased with `A`.


See also [`tensorcopy`](@ref) and [`tensoradd!`](@ref)
