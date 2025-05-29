```julia
nanlogcumsumexp(A)
```

`exp.(A)`の累積和の対数を返します。すなわち、`log.(cumsum.(exp.(A)))`ですが、`NaN`を無視し、数値のオーバーフロー/アンダーフローを回避します。`nancumsum`のように、対数で操作します。`nanlogsumexp`のように、単一の値ではなく、累積和の配列を返します。

## 例

```julia

```
