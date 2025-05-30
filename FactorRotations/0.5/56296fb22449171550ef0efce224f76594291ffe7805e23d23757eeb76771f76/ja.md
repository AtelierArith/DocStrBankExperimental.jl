```
Concave(bandwidth = 1)
```

単純な凹型 [component loss](@ref AbstractComponentLoss) 要因回転基準。損失関数は次のようになります。

$$
h(\lambda) = 1 - \exp(-\frac{|\lambda|}{b}),
$$

ここで、$b$ は *bandwidth* パラメータです。
