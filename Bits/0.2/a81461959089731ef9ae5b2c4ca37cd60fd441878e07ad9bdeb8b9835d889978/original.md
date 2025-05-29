```
masked(x, [j::Integer], i::Integer) -> typeof(x)
```

Return the result of applying the mask `mask(x, [j], i)` to `x`, i.e. `x & mask(x, [j], i)`. If `x` is a float, apply the mask to the underlying bits.

# Examples

```jldoctest
julia> masked(0b11110011, 1, 5) === 0b00010010
true

julia> x = rand(); masked(-x, 0, 63) === x
true
```
