```
low0(x, n::Integer=1)
low1(x, n::Integer=1)
```

Return the position of the `n`th `0` (for `low0`) or `1` (for `low1`) in `x.

# Examples

```jldoctest
julia> low0(0b10101, 2)
4

julia> low1(0b10101, 4) == Bits.NOTFOUND
true
```
