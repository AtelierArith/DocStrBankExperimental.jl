```
has_finite_multiplicative_order(M::Union{ZZMatrix, QQMatrix}) -> Bool
```

整数または有理数のエントリを持つ行列 `M` が与えられたとき、`M` が有限の乗法的順序を持つかどうかを返します。

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

julia> has_finite_multiplicative_order(M)
true

julia> N = matrix(ZZ, 2, 2, [1 1;
                             0 1])
[1   1]
[0   1]

julia> has_finite_multiplicative_order(N)
false
```
