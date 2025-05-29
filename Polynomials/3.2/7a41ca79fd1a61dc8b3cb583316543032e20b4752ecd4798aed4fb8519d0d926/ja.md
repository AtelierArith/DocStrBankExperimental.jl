```
Polynomial{T, X}(coeffs::AbstractVector{T}, [var = :x])
```

係数 `coeffs` から多項式を構築します。最低次が最初で、オプションで与えられた変数 `var` に関して構築されます。`var` は文字、シンボル、または文字列である可能性があります。

もし $p = a_n x^n + \ldots + a_2 x^2 + a_1 x + a_0$ であれば、`Polynomial([a_0, a_1, ..., a_n])` を通じてこれを構築します。

通常の算術演算子は、多項式とスカラーの組み合わせだけでなく、多項式同士でも動作するようにオーバーロードされています。ただし、異なる変数の2つの多項式を含む演算は、定数多項式を含む場合を除いてエラーを引き起こします。

!!! note
    `Polynomial` は軸を意識しておらず、`coeffs` を単に係数のリストとして扱い、最初のインデックスは常に定数項に対応します。`coeffs` の軸を指数として使用するには、[`LaurentPolynomial`](@ref) またはおそらく [`SparsePolynomial`](@ref) の使用を検討してください。


# 例

```jldoctest
julia> using Polynomials

julia> Polynomial([1, 0, 3, 4])
Polynomial(1 + 3*x^2 + 4*x^3)

julia> Polynomial([1, 2, 3], :s)
Polynomial(1 + 2*s + 3*s^2)

julia> one(Polynomial)
Polynomial(1.0)
```
