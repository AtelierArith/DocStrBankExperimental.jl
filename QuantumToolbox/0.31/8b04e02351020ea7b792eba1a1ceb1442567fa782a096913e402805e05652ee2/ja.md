```
squeeze(N::Int, z::Number)
```

単一モードの [squeeze operator](https://en.wikipedia.org/wiki/Squeeze_operator) を生成します：

$$
\hat{S}(z)=\exp\left( \frac{1}{2} (z^* \hat{a}^2 - z(\hat{a}^\dagger)^2) \right),
$$

ここで、$\hat{a}$ はボソニック消滅演算子です。
