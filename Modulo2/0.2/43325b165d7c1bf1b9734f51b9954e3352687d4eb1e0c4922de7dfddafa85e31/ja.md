```
rcef(b::ZZ2Matrix; reduced = true) -> ZZ2Matrix
```

行列 `b` のランク `r` とその列エシェロン形式 `c` のタプル `(r, c)` を返します。`reduced` が `true` の場合、縮約列エシェロン形式が計算されます。

[`rref`](@ref) や [`rcef!`](@ref) も参照してください。

# 例

```jldoctest
julia> a = ZZ2Matrix([1 0 0; 1 1 1])
2×3 ZZ2Matrix:
 1  0  0
 1  1  1

julia> rcef(a)
(2, ZZ2[1 0 0; 0 1 0])

julia> rcef(a; reduced = false)
(2, ZZ2[1 0 0; 1 1 0])
```
