```
pseudo_inv(x::ZZMatrix)
```

行列 $z$ と分母 $d$ からなるタプル $(z, d)$ を返します。ここで、$z/d$ は $x$ の逆行列です。

# 例

```jldoctest
julia> A = ZZ[1 0 1; 2 3 1; 5 6 7]
[1   0   1]
[2   3   1]
[5   6   7]

julia> B, d = pseudo_inv(A)
([15 6 -3; -9 2 1; -3 -6 3], 12)
```
