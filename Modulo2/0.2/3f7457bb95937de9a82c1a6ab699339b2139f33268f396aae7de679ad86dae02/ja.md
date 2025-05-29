```
rref(b::ZZ2Matrix; reduced = true) -> ZZ2Matrix
```

タプル `(r, c)` を返します。ここで `r` は行列 `b` のランクであり、`c` はその行基本形です。`reduced` が `true` の場合、簡約行基本形が計算されます。

（簡約）*列*基本形を計算するには `rcef` を使用する方が効率的です。

[`rcef`](@ref) も参照してください。

# 例

```jldoctest
julia> a = ZZ2Matrix([1 1; 0 1; 0 1])
3×2 ZZ2Matrix:
 1  1
 0  1
 0  1

julia> rref(a)
(2, ZZ2[1 0; 0 1; 0 0])

julia> rref(a; reduced = false)
(2, ZZ2[1 1; 0 1; 0 0])
```
