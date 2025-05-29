```julia
struct FlattenDefault{T<:AbstractFloat, F<:ModelWrappers.FlattenTypes}
```

フラット関数のデフォルト引数。

# フィールド

  * `output::Type{T} where T<:AbstractFloat`: フラット出力の型
  * `flattentype::ModelWrappers.FlattenTypes`: すべての入力がフラット化されるか（FlattenAll）または連続値のみがフラット化されるか（FlattenContinuous）を決定します。
