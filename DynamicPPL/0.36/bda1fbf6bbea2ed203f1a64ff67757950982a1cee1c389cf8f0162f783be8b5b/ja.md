```
invlink([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
invlink([t::AbstractTransformation, ]vi::AbstractVarInfo, vns::NTuple{N,VarName}, model::Model)
```

`vi`内の変数を変更せずに、その制約された空間に変換します。

すべての変数を変換するか、または`vns`で指定された変数のみを変換します。

提供されていない場合は、変換`t`の（逆）を使用するか、`default_transformation(model, vi)`を使用します。

関連情報: [`default_transformation`](@ref), [`link`](@ref).
