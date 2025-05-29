```
monomials(x::AbstractVector{String}, d::Integer, mo::MonomialOrder; include_zero::Bool=false)
```

変数 `x` のすべてのモノミアルを次数 `d` まで計算し、モノミアル順序 `mo` で並べます。

ゼロ次数のモノミアルを含めるには、`include_zero=true` を指定します。

# 例

```julia-repl
julia> monomials(["x","y"], 2, LexicographicOrder(); include_zero=true)
5-element Vector{Monomial}:
1
y
 y²
 x
 xy
 x²
```
