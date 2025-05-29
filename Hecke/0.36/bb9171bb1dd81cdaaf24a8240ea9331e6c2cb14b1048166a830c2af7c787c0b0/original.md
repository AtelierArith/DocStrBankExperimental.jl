```
saturate(A::ZZMatrix) -> ZZMatrix
```

Computes the saturation of $A$, that is, a basis for $\mathbf{Q}\otimes M \cap \mathbf{Z}^n$, where $M$ is the row span of $A$ and $n$ the number of columns of $A$.

Equivalently, return $TA$ (minus zero rows) for an invertible rational matrix $T$ such that $TA$ is integral and the elementary divisors of $TA$ are all trivial.

# Examples

```jldoctest
julia> saturate(ZZ[1 2 3;4 5 6;7 0 7])
[1    2    3]
[1    1    1]
[0   -1   -1]

julia> saturate(ZZ[1 2 3;4 5 6;7 8 9])
[1   2   3]
[1   1   1]

julia> saturate(ZZ[1 2 3;4 5 6])
[1   2   3]
[1   1   1]

julia> saturate(ZZ[1 2;3 4;5 6])
[1   2]
[1   1]

```
