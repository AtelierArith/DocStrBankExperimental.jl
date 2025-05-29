```
collectdnPl(x; lmax::Integer, n::Integer)
```

引数 `x` に対するレジェンドル多項式 $P_\ell(x)$ の $n$-次導関数をすべての次数 `l = 0:lmax` に対して計算します。

導関数の次数 `n` はゼロ以上でなければなりません。

インデックス `0:lmax` を持つ `v` を返します。ここで `v[l] == dnPl(x, l, n)` です。

# 例

```jldoctest
julia> collectdnPl(0.5, lmax = 3, n = 2)
4-element OffsetArray(::Vector{Float64}, 0:3) with eltype Float64 with indices 0:3:
 0.0
 0.0
 3.0
 7.5
```
