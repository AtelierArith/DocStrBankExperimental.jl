```
AbstractPolynomialZonotope{N} <: LazySet{N}
```

多項式ゾノトープ集合のための抽象型。

### 注意事項

このインターフェースの標準実装については、[`DensePolynomialZonotope`](@ref)を参照してください。

多項式ゾノトープは一般に非凸です。常に有界です。

具体的な`AbstractPolynomialZonotope`は、以下の関数を定義する必要があります：

  * `center(::AbstractPolynomialZonotope)` – 中心を返す
  * `polynomial_order(::AbstractPolynomialZonotope)` – 多項式の次数を返す
  * `ngens_dep` – 依存生成子の数を返す
  * `ngens_indep` – 独立生成子の数を返す

`AbstractPolynomialZonotope`のサブタイプ（抽象インターフェースを含む）：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolynomialZonotope)
2-element Vector{Any}:
 AbstractSparsePolynomialZonotope
 DensePolynomialZonotope
```
