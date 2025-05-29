```
link([t::AbstractTransformation, ]vi::AbstractVarInfo, model::Model)
link([t::AbstractTransformation, ]vi::AbstractVarInfo, spl::AbstractSampler, model::Model)
```

`vi`の変数を、`t`を使用してリンクされた空間に変換しますが、`vi`を変更することはありません。

`t`が提供されていない場合、`default_transformation(model, vi)`が使用されます。

参照: [`default_transformation`](@ref), [`invlink`](@ref).
