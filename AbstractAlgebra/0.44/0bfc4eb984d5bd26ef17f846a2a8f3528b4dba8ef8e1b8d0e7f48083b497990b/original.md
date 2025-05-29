```
diagonal_matrix(x::NCRingElement, m::Int, [n::Int])
```

Return the $m \times n$ matrix over $R$ with `x` along the main diagonal and zeroes elsewhere. If `n` is not specified, it defaults to `m`.

# Examples

```jldoctest
julia> diagonal_matrix(ZZ(2), 2, 3)
[2   0   0]
[0   2   0]

julia> diagonal_matrix(QQ(-1), 3)
[-1//1    0//1    0//1]
[ 0//1   -1//1    0//1]
[ 0//1    0//1   -1//1]
```
