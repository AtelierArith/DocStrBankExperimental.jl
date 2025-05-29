```
delete(model::Model, con_refs::Vector{<:ConstraintRef})
```

`con_refs` に関連付けられた制約をモデル `model` から削除します。ソルバーは、同じ具体的な型の複数の制約を削除するための特化したメソッドを実装する場合があります。すなわち、`isconcretetype(eltype(con_refs))` の場合です。これらは、単一の制約削除メソッドを繰り返し呼び出すよりも効率的である可能性があります。

参照: [`unregister`](@ref)
