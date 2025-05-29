```
conjugate(G::AbstractLieGroup, g, h)
conjugate!(G::AbstractLieGroup, k, g, h)
```

共役写像 $c_g: \mathcal G → \mathcal G$ を計算します。これは $c_g(h) = g∘h∘g^{-1}$ で与えられます。これは `k` のインプレースで行うことができます。
