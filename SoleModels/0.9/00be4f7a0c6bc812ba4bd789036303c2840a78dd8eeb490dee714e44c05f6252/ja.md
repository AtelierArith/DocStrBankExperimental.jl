```
iscomplete(::AbstractModel)::Bool
```

モデルが完全であるかどうかを返します。

[`AbstractModel`](@ref) は *完全* である場合、常に `O` 型の結果を提供できる必要があります。そうでない場合、モデルは `nothing` 値を出力することができ、*不完全* と呼ばれます。

[`Rule`](@ref) は *不完全* モデルの例であり、[`Branch`](@ref) は *完全* モデルの例です。

さらに [`AbstractModel`](@ref) を参照してください。
