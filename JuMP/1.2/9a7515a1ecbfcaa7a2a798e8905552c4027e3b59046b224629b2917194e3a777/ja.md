```
delete(model::Model, variable_refs::Vector{VariableRef})
```

`variable_refs`に関連付けられた変数をモデル`model`から削除します。ソルバーは、単一の変数削除メソッドを繰り返し呼び出すよりも効率的な複数の変数を削除するメソッドを実装することがあります。

関連情報: [`unregister`](@ref)
