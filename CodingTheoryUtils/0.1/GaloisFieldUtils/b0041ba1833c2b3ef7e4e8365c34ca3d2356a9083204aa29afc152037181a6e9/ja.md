```
polynomial_from_roots(r::AbstractVector{T}, var::Polynomials.SymbolLike=:x)::Polynomial{T} where {T}
```

根から多項式を生成します。

# 引数

  * `r`: 根の配列
  * `var`: 多項式の変数シンボル（デフォルト: :x）

# 戻り値

  * `Polynomial{T}`: 指定された根を持つ多項式

# 例

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> roots = [α, α^2]
julia> polynomial_from_roots(roots)
Polynomial(1 + x + x^2)
```
