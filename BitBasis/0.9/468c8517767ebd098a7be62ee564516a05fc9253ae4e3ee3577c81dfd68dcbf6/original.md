```
swapbits(n::Integer, mask_ij::Integer) -> Integer
swapbits(n::Integer, i::Int, j::Int) -> Integer
```

Return an integer with bits at `i` and `j` flipped.

# Example

```jldoctest
julia> swapbits(0b1011, 0b1100) == 0b0111
true
```

!!! tip
    locations `i` and `j` specified by mask could be faster when [`bmask`](@ref) is not straight forward but known by constant.


!!! warning
    `mask_ij` should only contain two `1`, `swapbits` will not check it, use at your own risk.

