```
invlink!!([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
invlink!!([t::AbstractTransformation, ]vi::AbstractVarInfo, vns::NTuple{N,VarName}, model::Model)
```

`vi`内の変数を制約された空間に変換し、可能であれば`vi`を変更します。

すべての変数を変換するか、または`vns`で指定された変数のみを変換します。

提供されていない場合は、変換`t`の（逆）または`default_transformation(model, vi)`を使用します。

関連情報: [`default_transformation`](@ref), [`link!!`](@ref).
