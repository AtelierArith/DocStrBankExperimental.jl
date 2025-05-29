```
link!!([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
link!!([t::AbstractTransformation, ]vi::AbstractVarInfo, vns::NTuple{N,VarName}, model::Model)
```

`vi`内の変数をリンクされた空間に変換し、可能であれば`vi`を変更します。

すべての変数を変換するか、または`vns`で指定された変数のみを変換します。

変換`t`を使用するか、提供されていない場合は`default_transformation(model, vi)`を使用します。

参照: [`default_transformation`](@ref), [`invlink!!`](@ref).
