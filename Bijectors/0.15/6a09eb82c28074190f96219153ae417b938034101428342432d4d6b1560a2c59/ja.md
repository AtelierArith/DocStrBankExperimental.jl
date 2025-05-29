```
with_logabsdet_jacobian!(b, x[, y, logjac])
```

`transform(b, x)` と `logabsdetjac(b, x)` を計算し、結果をそれぞれ `y` と `logjac` に格納します。

`y` が提供されていない場合、`x` がその代わりに使用されます。

デフォルトでは `with_logabsdet_jacobian(b, x)` を呼び出し、結果で `y` と `logjac` を更新します。
