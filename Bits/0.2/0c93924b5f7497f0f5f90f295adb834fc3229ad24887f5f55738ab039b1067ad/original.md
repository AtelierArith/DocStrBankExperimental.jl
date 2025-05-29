```
scan0(x, n::Integer=1)
scan1(x, n::Integer=1)
```

Return the position of the first `0` (for `scan0`) or `1` (for `scan1`) after or including `n` in `x`.

# Examples

```jldoctest
julia> scan0(0b10101, 1)
2

julia> scan1(0b10101, 6) == Bits.NOTFOUND
true
```
