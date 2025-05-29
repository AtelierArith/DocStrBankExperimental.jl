```
SKPreprocessor(preprocessor::String,args::Dict=Dict())
```

Scikitlearnの前処理関数のラッパーです。 `skpreprocessors()`を呼び出すと、受け入れ可能でサポートされている関数のリストが表示されます。渡す引数についてはScikitlearnのドキュメントを確認してください。

`fit!`と`transform!`を実装しています。
