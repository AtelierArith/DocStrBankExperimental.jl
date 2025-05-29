```
truncate(a::AbstractAlgebra.AbsMSeries, prec::Int)
```

精度 `prec` に切り詰められた $a$ を返します。これは、重み付きの場合は重みによって切り詰められ、重みなしの場合は各変数を精度 `prec` に切り詰めます。
