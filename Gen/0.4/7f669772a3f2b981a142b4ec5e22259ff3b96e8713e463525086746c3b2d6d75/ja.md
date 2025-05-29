```
grads::Tuple = logpdf_grad(dist::Distribution{T}, value::T, args...)
```

値および各引数に関するlogpdfの勾配を計算します。

`has_output_grad`がfalseを返す場合、返されるタプルの最初の要素は`nothing`です。それ以外の場合、タプルの最初の要素は値に関する勾配です。`has_argument_grads`の返り値が位置`i`でfalseの値を持つ場合、返されるタプルの`i+1`番目の要素は`nothing`の値を持ちます。それ以外の場合、この要素は`i`番目の引数に関する勾配を含みます。
