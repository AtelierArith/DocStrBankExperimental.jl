```
link([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
link([t::AbstractTransformation, ]vi::AbstractVarInfo, vns::NTuple{N,VarName}, model::Model)
```

`vi`内の変数を変更せずに、それらのリンクされた空間に変換します。

すべての変数を変換するか、`vns`で指定された変数のみを変換します。

`t`という変換を使用するか、提供されていない場合は`default_transformation(model, vi)`を使用します。

関連情報: [`default_transformation`](@ref), [`invlink`](@ref).
