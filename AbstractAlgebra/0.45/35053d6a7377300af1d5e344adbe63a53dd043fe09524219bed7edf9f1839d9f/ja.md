```
is_skew_symmetric(M::MatrixElem)
```

与えられた行列が主対角線に関して反対称である場合は `true` を返します。すなわち、`transpose(M) == -M` の場合です。それ以外の場合は `false` を返します。

# 例

```jldoctest
julia> M = matrix(ZZ, [0 -1 -2; 1 0 -3; 2 3 0])
[0   -1   -2]
[1    0   -3]
[2    3    0]

julia> is_skew_symmetric(M)
true

```
