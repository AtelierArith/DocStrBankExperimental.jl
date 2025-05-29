```
blockkron(A...)
```

Return a blocked version of kron(A...) with the natural block-structure imposed.

# Examples

```jldoctest
julia> A = reshape(1:9, 3, 3)
3×3 reshape(::UnitRange{Int64}, 3, 3) with eltype Int64:
 1  4  7
 2  5  8
 3  6  9

julia> BlockArrays.blockkron(A, A)
3×3-blocked 9×9 BlockMatrix{Int64}:
 1   4   7  │   4  16  28  │   7  28  49
 2   5   8  │   8  20  32  │  14  35  56
 3   6   9  │  12  24  36  │  21  42  63
 ───────────┼──────────────┼────────────
 2   8  14  │   5  20  35  │   8  32  56
 4  10  16  │  10  25  40  │  16  40  64
 6  12  18  │  15  30  45  │  24  48  72
 ───────────┼──────────────┼────────────
 3  12  21  │   6  24  42  │   9  36  63
 6  15  24  │  12  30  48  │  18  45  72
 9  18  27  │  18  36  54  │  27  54  81
```
