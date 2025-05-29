```
hex(n::ZZRingElem) = base(n, 16)
```

Return $n$ as a hexadecimal string.

# Examples

```jldoctest
julia> hex(ZZ(12))
"c"
```
