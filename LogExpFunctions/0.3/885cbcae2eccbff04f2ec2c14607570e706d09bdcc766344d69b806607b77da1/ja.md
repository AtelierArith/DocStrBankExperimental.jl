```julia
logabssinh(x)

```

`log(abs(sinh(x)))`を返します。`sinh(x)`の中間計算を行わずに慎重に評価されます。

実装は`logabssinh(-x) = logabssinh(x)`を保証します。
