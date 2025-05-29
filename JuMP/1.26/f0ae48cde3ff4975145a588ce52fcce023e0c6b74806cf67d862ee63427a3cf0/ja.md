```
mutable struct GenericAffExpr{CoefType,VarType} <: AbstractJuMPScalar
    constant::CoefType
    terms::OrderedDict{VarType,CoefType}
end
```

アフィン表現の形式を表す式タイプ: $\sum a_i x_i + c$。

## フィールド

  * `.constant`: 式の定数 `c`。
  * `.terms`: `OrderedDict`、キーは `VarType`、値は `CoefType` で、スパースベクトル `a` を説明します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> expr = x[2] + 3.0 * x[1] + 4.0
x[2] + 3 x[1] + 4

julia> expr.constant
4.0

julia> expr.terms
OrderedCollections.OrderedDict{VariableRef, Float64} with 2 entries:
  x[2] => 1.0
  x[1] => 3.0
```
