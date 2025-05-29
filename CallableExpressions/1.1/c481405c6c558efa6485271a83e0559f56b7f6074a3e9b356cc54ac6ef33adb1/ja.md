```
expression_new(expression_type::Type, operation, children, metadata)
```

`expression_type`に基づいた型の式を返しますが、`children`をその即時の子として、`operation`を最上位の操作として持ちます。

`metadata`引数は追加の必要なデータを持つことがあります。デフォルトでは`nothing`を使用します。
