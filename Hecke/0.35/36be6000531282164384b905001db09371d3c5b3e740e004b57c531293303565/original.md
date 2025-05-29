```
multiplicative_order(M::Union{ZZMatrix, QQMatrix}) -> IntExt
```

Given a matrix `M` with integral or rational entries, return the multiplicative order of `M`. Note that this can be infinite, in which case the function returns `PosInf()`.

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

julia> multiplicative_order(M)
4

julia> N = matrix(ZZ, 2, 2, [1 1;
                             0 1])
[1   1]
[0   1]

julia> multiplicative_order(N)
infinity
```
