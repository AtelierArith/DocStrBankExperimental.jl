```
evaljs_value(session::Session, js::JSCode)
```

`js` コードを評価し、jsonified 値を返します。値が返されるまでブロックします。ブラウザへの接続がないセッションで呼び出された場合、無期限にブロックする可能性があります。
