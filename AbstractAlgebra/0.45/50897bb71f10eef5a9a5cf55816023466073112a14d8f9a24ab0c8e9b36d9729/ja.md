```
is_symmetric(M::MatrixElem)
```

与えられた行列が主対角線に関して対称である場合は `true` を返します。すなわち、`transpose(M) == M` の場合です。それ以外の場合は `false` を返します。

`LinearAlgebra.issymmetric` のエイリアスです。

# 例

```jldoctest
julia> M = matrix(ZZ, [1 2 3; 2 4 5; 3 5 6])
[1   2   3]
[2   4   5]
[3   5   6]

julia> is_symmetric(M)
true

julia> N = matrix(ZZ, [1 2 3; 4 5 6; 7 8 9])
[1   2   3]
[4   5   6]
[7   8   9]

julia> is_symmetric(N)
false
```
