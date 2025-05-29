```
mutable struct GenericAffExpr{CoefType,VarType} <: AbstractJuMPScalar
    constant::CoefType
    terms::OrderedDict{VarType,CoefType}
end
```

アフィン表現の形式を表す式タイプ: $\sum a_i x_i + c$。

## フィールド

  * `.constant`: 式の定数 `c`。
  * `.terms`: `VarType` のキーと `CoefType` の値を持つ `OrderedDict` で、スパースベクトル `a` を説明します。
