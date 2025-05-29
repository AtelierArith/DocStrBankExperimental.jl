```
derivative_at(x::Real, values, nodes, baryweights)
```

`values`で表される関数の導関数を、対応する重心重み`baryweights`を使用して、`nodes`の`x`で計算します。[Kopriva, Implementing Spectral Methods for PDEs, Algorithm 36].
