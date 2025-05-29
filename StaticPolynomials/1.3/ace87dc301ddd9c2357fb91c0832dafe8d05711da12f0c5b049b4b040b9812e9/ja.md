```
PolynomialSystem{N, NVars, NParams, <:Tuple}
```

`N` 個の多項式からなる多項式系で、`NVars` 変数と `NParams` 変数を持ちます。

コンストラクタ:

```
PolynomialSystem(polys::AbstractVector{<:MP.AbstractPolynomial}; variables=MP.variables(polys), parameters=nothing)
PolynomialSystem(polys::MP.AbstractPolynomial...; kwargs...)
```

与えられた多項式 `polys` から多項式系を作成します。この関数は設計上、型安定ではありません。

## 例

```julia
julia> import DynamicPolynomials: @polyvar
julia> @polyvar x y a
julia> PolynomialSystem(x^2+y^2+3, x-y+2, x^2+2y+a; parameters=[a])
PolynomialSystem{3, 2}:
 3 + x² + y²

 2 + x - y

 x² + 2y

```
