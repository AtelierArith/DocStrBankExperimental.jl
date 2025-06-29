```
mod1(x, y)
```

床除算の後の剰余を返し、正の `y` に対しては範囲 $(0, y]$ で、負の `y` に対しては範囲 $[y,0)$ で `mod(r, y) == mod(x, y)` となる値 `r` を返します。

整数引数と正の `y` の場合、これは `mod(x, 1:y)` と等しく、したがって1ベースのインデックスに対して自然です。比較すると、`mod(x, y) == mod(x, 0:y-1)` はオフセットやストライドを伴う計算に対して自然です。

他にも [`mod`](@ref)、[`fld1`](@ref)、[`fldmod1`](@ref) を参照してください。

# 例

```jldoctest
julia> mod1(4, 2)
2

julia> mod1.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  3  1  2  3  1  2  3  1  2

julia> mod1.([-0.1, 0, 0.1, 1, 2, 2.9, 3, 3.1]', 3)
1×8 Matrix{Float64}:
 2.9  3.0  0.1  1.0  2.0  2.9  3.0  0.1
```
