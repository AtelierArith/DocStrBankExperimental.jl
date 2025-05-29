```
AbstractSparsePolynomialZonotope{N} <: AbstractPolynomialZonotope{N}
```

スパース多項式ゾノトープ集合のための抽象型。

### 注意事項

このインターフェースの標準実装については、[`SparsePolynomialZonotope`](@ref)を参照してください。

すべての具体的な`AbstractSparsePolynomialZonotope`は、以下の関数を定義する必要があります：

  * `expmat(::AbstractSparsePolynomialZonotope)` – 指数行列を返す（スパースPZのみ）
  * `genmat_dep(::AbstractSparsePolynomialZonotope)` – 従属生成子の行列を返す
  * `genmat_indep(::AbstractSparsePolynomialZonotope)` – 独立生成子の行列を返す

`AbstractSparsePolynomialZonotope`のサブタイプ（抽象インターフェースを含む）：

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractSparsePolynomialZonotope)
2-element Vector{Any}:
 SimpleSparsePolynomialZonotope
 SparsePolynomialZonotope
```
