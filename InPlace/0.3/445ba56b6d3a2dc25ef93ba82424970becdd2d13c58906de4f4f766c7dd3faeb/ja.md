```
@inplace a = f(args...)
@inplace a += expr
```

`f(args...)` および `+(a, expr)` を計算し、その結果を `a` に代入します。もし `a` が可変であれば、その値をインプレースで変更する可能性があります。

`a` が可変である場合、その値が実際に変更されるかどうかは実装の詳細です。このため、この操作は現在のスタックフレームが唯一の参照を保持している値に対してのみ使用するべきです。例えば、`deepcopy` を使用することによってです。
