```
src, line1 = definition(String, method::Method)
```

`method`を定義するコードを含む文字列を返します。また、定義の最初の行（署名を含む）も返します（これは`whereis`によって返される行番号と同じでない場合があります）。もしメソッドが見つからない場合（行番号が0の場合）、`definition`は代わりに`nothing`を返します。

これは`@eval`文の内部で定義されたメソッドにはあまり役に立たないかもしれません。代わりに[`definition(Expr, method::Method)`](@ref)を参照してください。

また[`code_string`](@ref)も参照してください。
