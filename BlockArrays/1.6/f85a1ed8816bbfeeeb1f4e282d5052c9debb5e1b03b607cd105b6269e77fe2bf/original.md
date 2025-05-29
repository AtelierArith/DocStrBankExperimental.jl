```
blockcheckbounds(A, inds...)
```

Throw a `BlockBoundsError` if the specified block indexes are not in bounds for the given block array. Subtypes of `AbstractBlockArray` should specialize this method if they need to provide custom block bounds checking behaviors.

```jldoctest
julia> A = BlockArray(rand(2,3), [1,1], [2,1]);

julia> blockcheckbounds(A, 3, 2)
ERROR: BlockBoundsError: attempt to access 2×2-blocked 2×3 BlockMatrix{Float64} at block index [3,2]
[...]
```
