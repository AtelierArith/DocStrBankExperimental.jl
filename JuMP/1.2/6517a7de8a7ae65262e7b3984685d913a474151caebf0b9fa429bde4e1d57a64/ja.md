```
add_to_expression!(expression, terms...)
```

`expression`を*その場で* `expression + (*)(terms...)`に更新します。これは通常、`expression += (*)(terms...)`よりもはるかに効率的です。例えば、`add_to_expression!(expression, a, b)`は`expression += a*b`と同じ結果を生成し、`add_to_expression!(expression, a)`は`expression += a`と同じ結果を生成します。

定義されているメソッドはごくわずかで、主に内部使用のためであり、(1) 効率的に実装できる場合と (2) `expression`が結果を格納できる場合に限られます。例えば、`add_to_expression!(::AffExpr, ::VariableRef, ::VariableRef)`は定義されていません。なぜなら、`GenericAffExpr`は二つの変数の積を格納できないからです。
