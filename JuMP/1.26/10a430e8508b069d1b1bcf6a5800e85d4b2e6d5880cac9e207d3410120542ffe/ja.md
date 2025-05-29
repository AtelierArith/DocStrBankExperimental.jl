```
mutable struct GenericQuadExpr{CoefType,VarType} <: AbstractJuMPScalar
    aff::GenericAffExpr{CoefType,VarType}
    terms::OrderedDict{UnorderedPair{VarType}, CoefType}
end
```

二次式の形を表す式の型: $\sum q_{i,j} x_i x_j + \sum a_i x_i + c$。

## フィールド

  * `.aff`: 式のアフィン部分を表す [`GenericAffExpr`](@ref)。
  * `.terms`: `UnorderedPair{VarType}` のキーと `CoefType` の値を持つ `OrderedDict` で、スパースな項のリスト `q` を記述します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = 2.0 * x[1]^2 + x[1] * x[2] + 3.0 * x[1] + 4.0
2 x[1]² + x[1]*x[2] + 3 x[1] + 4

julia> expr.aff
3 x[1] + 4

julia> expr.terms
OrderedCollections.OrderedDict{UnorderedPair{VariableRef}, Float64} with 2 entries:
  UnorderedPair{VariableRef}(x[1], x[1]) => 2.0
  UnorderedPair{VariableRef}(x[1], x[2]) => 1.0
```
