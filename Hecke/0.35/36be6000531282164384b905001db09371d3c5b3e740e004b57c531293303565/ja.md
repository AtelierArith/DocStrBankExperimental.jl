```
multiplicative_order(M::Union{ZZMatrix, QQMatrix}) -> IntExt
```

整数または有理数のエントリを持つ行列 `M` が与えられたとき、`M` の乗法的順序を返します。この値は無限である可能性があり、その場合、関数は `PosInf()` を返します。

# 例

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
