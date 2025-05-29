```
frame = Frame(mod::Module, ex::Expr)
```

モジュール `mod` で `ex` を評価するための `Frame` を構築します。

このコンストラクタはエラーを引き起こす可能性があります。たとえば、`ex` の低下が `:error` または `:incomplete` 式を結果として返す場合や、その他の理由で `:thunk` を返さない場合です。
