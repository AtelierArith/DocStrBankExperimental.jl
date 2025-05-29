```
basis_covering_monomials(B::Type{<:AbstractPolynomialBasis}, monos::AbstractVector{<:AbstractMonomial})
```

モノミアル基底 `monos` によって生成されるすべての多項式を生成できるタイプ `B` の最小基底を返します。

## 例

たとえば、モノミアル `x^4` と `x^2` の係数が非ゼロのすべての多項式を生成するには、3つの多項式が必要です。そうしないと、非ゼロの定数項を持つ多項式が生成されます。

```jldoctest
julia> using DynamicPolynomials

julia> @polyvar x
(x,)

julia> basis_covering_monomials(ChebyshevBasis, [x^2, x^4])
ChebyshevBasisFirstKind([1.0, -1.0 + 2.0x², 1.0 - 8.0x² + 8.0x⁴])
```
