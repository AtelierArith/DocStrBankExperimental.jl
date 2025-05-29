```
superscript(i::Rational; io::Union{IO, Nothing} = nothing)
```

指数を文字列として返します。

この関数は値を文字列として返します。`io` に出力は行いません。`io` は IO コンテキスト値のためだけに使用されます。`io` に `:fancy_exponent` プロパティが含まれ、その値が `Bool` の場合、この値はファンシー指数の動作を上書きします。
