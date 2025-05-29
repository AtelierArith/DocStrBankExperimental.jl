```
expression_into_type_domain(expression)
```

`expression`と等しいが、そのデータが型ドメインに完全に含まれる式を返します。

Juliaが関連する値を型パラメータとして使用できない場合、例外をスローする可能性があります。

任意の有効な`expr`に対して満たされるべきいくつかの性質：

  * `Base.issingletontype(typeof(expression_into_type_domain(expr)))`
  * `expr == expression_into_type_domain(expr)`
