```
pseudo_inv(x::ZZMatrix)
```

Return a tuple $(z, d)$ consisting of a matrix $z$ and denominator $d$ such that $z/d$ is the inverse of $x$.

# Examples

```jldoctest
julia> A = ZZ[1 0 1; 2 3 1; 5 6 7]
[1   0   1]
[2   3   1]
[5   6   7]

julia> B, d = pseudo_inv(A)
([15 6 -3; -9 2 1; -3 -6 3], 12)
```
