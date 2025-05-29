```
mutable struct GenericQuadExpr{CoefType,VarType} <: AbstractJuMPScalar
    aff::GenericAffExpr{CoefType,VarType}
    terms::OrderedDict{UnorderedPair{VarType}, CoefType}
end
```

二次式の形を表す式の型: $\sum q_{i,j} x_i x_j + \sum a_i x_i + c$。

## フィールド

  * `.aff`: 式のアフィン部分を表す[`GenericAffExpr`](@ref)。
  * `.terms`: `UnorderedPair{VarType}`のキーと`CoefType`の値を持つ`OrderedDict`で、スパースな項のリスト`q`を説明します。
