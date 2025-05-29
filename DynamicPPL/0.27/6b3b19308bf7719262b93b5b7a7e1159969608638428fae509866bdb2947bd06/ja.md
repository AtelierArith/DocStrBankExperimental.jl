```
invlink([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
invlink([t::AbstractTransformation, ]vi::AbstractVarInfo, spl::AbstractSampler, model::Model)
```

`vi`の変数を、`vi`を変更せずに、変換`t`の（逆）を使用して制約された空間に変換します。

`t`が提供されていない場合、`default_transformation(model, vi)`が使用されます。

参照: [`default_transformation`](@ref), [`link`](@ref).
