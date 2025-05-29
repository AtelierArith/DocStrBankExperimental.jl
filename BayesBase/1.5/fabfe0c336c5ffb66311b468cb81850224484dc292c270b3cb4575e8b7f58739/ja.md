```
TerminalProdArgument(argument)
```

`TerminalProdArgument`は、特化されたラッパー構造体です。`prod`関数の引数として使用されると、製品戦略を考慮せずに自分自身を返し、安全チェック（例：`variate_form`や`support`）を行いません。`TerminalProdArgument`の2つのインスタンスの積を計算しようとすると、エラーが発生します。基になるラップされた引数を取得するには、`.argument`フィールドを使用してください。
