```
∂t(f::DerivableType, ::Val{k}) -> DerivableType
```

`f`の`k`階の時間微分演算子を構築します。

`time_derivative(f, Val(k))`のエイリアスです。
