```
has_finite_multiplicative_order(M::Union{ZZMatrix, QQMatrix}) -> Bool
```

Given a matrix `M` with integral or rational entries, return whether `M` has finite multiplicative order.

# Examples

```jldoctest
julia> M = matrix(QQ, 4, 4, [ 1  0  0  0;
                              0 -1  0  0;
                             -1  0 -1 -1;
                              1  1  2  1])
[ 1    0    0    0]
[ 0   -1    0    0]
[-1    0   -1   -1]
[ 1    1    2    1]

julia> has_finite_multiplicative_order(M)
true

julia> N = matrix(ZZ, 2, 2, [1 1;
                             0 1])
[1   1]
[0   1]

julia> has_finite_multiplicative_order(N)
false
```
