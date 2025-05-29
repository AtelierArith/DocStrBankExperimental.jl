```
conjugate(CircleGroup, g, h)
conjugate!(CircleGroup, k, g, h)
```

共役写像 $c_g: \mathcal G → \mathcal G$ を計算します。これは $c_g(h) = g∘h∘g^{-1} = h$ です。円群の群演算は可換であるため、単位元に簡略化されます。

`k` が `mutable` であれば、`k` のインプレースで計算できます。
